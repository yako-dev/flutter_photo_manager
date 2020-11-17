# CHANGELOG

- [CHANGELOG](#changelog)
  - [0.6.0-dev.6](#060-dev6)
  - [0.5.8](#058)
  - [0.5.7](#057)
  - [0.5.6](#056)
  - [0.5.5+1](#0551)
  - [0.5.5](#055)
  - [0.5.4](#054)
  - [0.5.3+1](#0531)
  - [0.5.3](#053)
  - [0.5.2](#052)
  - [0.5.1](#051)
  - [0.5.0](#050)
  - [0.4.8](#048)
  - [0.4.7](#047)
  - [0.4.6](#046)
  - [0.4.5](#045)
  - [0.4.4](#044)
  - [0.4.3](#043)
  - [0.4.2](#042)
  - [0.4.1](#041)
  - [0.4.0](#040)
  - [0.3.5](#035)
  - [0.3.4](#034)
  - [0.3.3](#033)
  - [0.3.2](#032)
  - [0.3.1](#031)
  - [0.3.0](#030)
  - [0.2.1](#021)
  - [0.2.0](#020)
  - [0.1.10](#0110)
  - [0.1.9](#019)
  - [0.1.8 sort asset by data](#018-sort-asset-by-data)
  - [0.1.7 fix bug](#017-fix-bug)
  - [0.1.6](#016)
  - [0.1.5](#015)
  - [0.1.4 fix bug](#014-fix-bug)
  - [0.1.3 add params](#013-add-params)
  - [0.1.2 fix bug](#012-fix-bug)
  - [0.1.1 fix ios video](#011-fix-ios-video)
  - [0.1.0 support video](#010-support-video)
  - [0.0.3 fix bug](#003-fix-bug)
  - [0.0.2 update readme](#002-update-readme)
  - [0.0.1](#001)

## 0.6.0-dev.6

- Feature

  - Support android API 30.
  - Support show empty album in iOS([#365](https://github.com/CaiJingLong/flutter_photo_manager/issues/365)).
  - User can ignore check permission(User can choose favorite permission plugin, but at the same time user have to bear the risks corresponding to the permission).
  - Support clean file cache.
  - Experimental
    - Preload image (Use `PhotoCachingManager` api.)
  - Add `OrderOption` as sort condition. The option default value is order by create date desc;

- Fixes
  - [#362](https://github.com/CaiJingLong/flutter_photo_manager/issues/362)
  - Delete assets in androidQ.

Breaking change:

- Feature
  - Support multiple sorting conditions, and the `asc` of `DateTimeCond` is removed.

## 0.5.8

Fix:

Delete assets in androidQ.

## 0.5.7

Fix:

- Audio asset error for androidQ. See [#340](https://github.com/CaiJingLong/flutter_photo_manager/issues/340) [#341](https://github.com/CaiJingLong/flutter_photo_manager/pull/341).

## 0.5.6

Fix save image with path for android.

## 0.5.5+1

Remove verbose log.

## 0.5.5

Add `merge` for `FilterOptionGroup` and `FilterOption` .

## 0.5.4

Add `copyWith` for `FilterOption` .

## 0.5.3+1

Support android v2 model.

## 0.5.3

Fix:

- Cannot get audio problem in androidQ.

## 0.5.2

Support MacOS

From the version, Starting from this version, 1.9 or earlier versions are not supported.

## 0.5.1

Feature:

- Save image asset with file path.
- Copy asset to another album.
- Create AssetEntity with id.
- Create AssetPathEntity from id.
- Only iOS
  - Create folder or album.
  - Remove assets in album.
  - Delete folder or album.
  - Favorite asset.
- Only android
  - move asset to another path.
  - Remove all non-existing rows.
  - add `relativePath` for android.

Fix:

- Problem of AssetPathEntity.refreshPathProperties.
- Open setting in iOS.
- Edited asset in iOS.
- Audio properties of FilterOption.
- Android onlyAll assetCount bug.

Change:

- Modified `AssetEntity.file`'s behavior on iOS, currently it will return a picture in jpg format instead of heic/gif/png. Now more in line with the description in the doc, this is suitable for uploading images (theoretically, no Exif information will be included).
- Update android change media url from file scheme to content scheme.
- Clean up some unused code.

## 0.5.0

Feature:

- Add `getSubPathEntities` for `AssetPathEntity`.
- Add `quality` for `AssetEntity.thumbDataWithSize`.
- Add `orientation` for `AssetEntity`.
- Add `onlyAll` for `getAssetPathList`.
- Support audio type(Only android, iOS Photos have no audio)
- **Breaking change**, Add date condition to filter datetime
  - Add class `DateTimeCond`
  - Add `dateTimeCond` to `FilterOptionGroup`
  - Remove `fetchDateTime` from `getAssetPathList`
  - Remove param `dt` from `AssetPathEntity.refreshPathProperties`, and add `refreshPathProperties` params to the method.

Update

- **Breaking change**, Split video filter and image filter
- iOS code is running background thread.
- getThumb is running in background thread.

Fix

- exists error on android.
- use edited origin file on iOS.
- galleryName maybe is null in android.
- thumb of android 10.

## 0.4.8

Fixes:

- [#169](https://github.com/CaiJingLong/flutter_photo_manager/issues/169)
- [#170](https://github.com/CaiJingLong/flutter_photo_manager/issues/170)

## 0.4.7

New feature:

- Add `FilterOption` for method `getAssetPathList`.

## 0.4.6

Fix:

- originFile of `AssetEntity`

Add:

- location(`latitude`,`longitude`) of `AssetEntity`
- `title` of `AssetEntity`
- `originBytes` of `AssetEntity`
- param `format` in `thumbDataWithSize` of assetEntity.

## 0.4.5

Fix:

- Can't get thumb/file of video on androidQ.

## 0.4.4

Fix:

- Compatibility code, when the width and height of the video is empty, it can still be scanned.
- Add a default value to `type` of `getAssetPathList`.

## 0.4.3

Add:

- Delete asset.
- Add Image.
- Add Video.
- Add modifiDate property.
- Fix videoDuration error.

Fix:

- CreateDate error.

## 0.4.2

- Fix ios get full file size error.

## 0.4.1

Fix:

- Fix ios build error.

## 0.4.0

Breaking change.

- Some properties in the entity were modified from asynchronous to synchronous.
- Remove `isCache` params. Now, `getAssetPathList` will reload info everytime. If user want to cache `List<AssetPathEntity>`, then user must do it self.

Added:

- Added a method `getAssetListPaged` for paging loading resources to path. The paging implementation is lazy loading, that is, the resource corresponding information is loaded when requested. The entity corresponding to the path is no longer placed in the memory, but is implemented by PHPhoto (ios) and sqlite's limit offset (android).
- Support AndroidQ privacy.

## 0.3.5

Fix

- ICloud image problem.

## 0.3.4

Support flutter 1.6.0 android's thread changes for channel.

## 0.3.3

Fix customizing album containing folders on iOS.

## 0.3.2

`AssetEntity` add property: `originFile`

## 0.3.1

`AssetEntity` add property: `exists`

## 0.3.0

- Support Android X.
- **Breaking change**. Migrate from the deprecated original Android Support Library to AndroidX. This shouldn't result in any functional changes, but it requires any Android apps using this plugin to also migrate if they're using the original support library.

fix NPE for image crash on android.

add a method to create `AssetEntity` with id

add `isCache` for method `getImageAsset`,`getVideoAsset` or `getAssetPathList`

add observer for photo change.

add field `createTime` for `AssetEntity`

## 0.2.1

add two method to load video / image

`getVideoAsset` `getImageAsset`

## 0.2.0

add asset size field

release cache method

## 0.1.10

fix

    when number of photo/video is 0, will crash

## 0.1.9

add video duration

## 0.1.8 sort asset by data

## 0.1.7 fix bug

fix bug: Android's latest picture won't be found

update gradle wrapper version.

update kotlin version

## 0.1.6

Fix Android to get pictures that are empty bug.

## 0.1.5

support ios icloud image and video

## 0.1.4 fix bug

update all path hasVideo property

## 0.1.3 add params

add a params to help user disable get video

## 0.1.2 fix bug

ios get video file is async

## 0.1.1 fix ios video

fix 'ios video full file is a jpg' problem

## 0.1.0 support video

support video in android.
and will change api from ImageXXXX to AssetXXXX

## 0.0.3 fix bug

update for the issue #1 (NPE when request other permission on android)

## 0.0.2 update readme

## 0.0.1

first version

api for photo
