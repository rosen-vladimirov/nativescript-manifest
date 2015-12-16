# nativescript-manifest
Sample application for merging AndroidManifest.xml files

## Prerequisite

Install latest `nativescript-cli` by executing `npm i -g nativescript`.


## Setup

1. Clone this repository: `git clone https://github.com/rosen-vladimirov/nativescript-manifest.git`
1. Open terminal/cmd and navigate to the cloned repository.
1. Go to sample directory: `cd sample`.
1. Build the application `tns build android`.

The produced `.apk` should have the following `AndroidManifest.xml`:
```xml
<?xml version="1.0" encoding="utf-8" standalone="no"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android" package="org.nativescript.nativescriptManifest" platformBuildVersionCode="22" platformBuildVersionName="5.1.1-1819727">
    <uses-permission android:name="android.permission.CAMERA"/>
    <uses-permission android:name="android.permission.FLASHLIGHT"/>
    <uses-feature android:name="android.hardware.camera" android:required="false"/>
    <supports-screens android:largeScreens="true" android:normalScreens="true" android:smallScreens="true" android:xlargeScreens="true"/>
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.INTERNET"/>
    <application android:allowBackup="true" android:debuggable="true" android:icon="@drawable/icon" android:label="@string/app_name" android:name="com.tns.NativeScriptApplication" android:theme="@style/AppTheme">
        <activity android:configChanges="keyboardHidden|orientation|screenSize" android:label="@string/title_activity_kimera" android:name="com.tns.NativeScriptActivity" android:windowSoftInputMode="stateHidden">
            <intent-filter>
                <action android:name="android.intent.action.MAIN"/>
                <category android:name="android.intent.category.LAUNCHER"/>
            </intent-filter>
        </activity>
        <activity android:clearTaskOnLaunch="true" android:configChanges="keyboardHidden|orientation" android:exported="false" android:name="com.google.zxing.client.android.CaptureActivity" android:theme="@android:style/Theme.NoTitleBar.Fullscreen" android:windowSoftInputMode="stateAlwaysHidden">
            <intent-filter>
                <action android:name="com.google.zxing.client.android.SCAN"/>
                <category android:name="android.intent.category.DEFAULT"/>
            </intent-filter>
        </activity>
        <activity android:name="com.tns.ErrorReportActivity"/>
    </application>
</manifest>
```

## Known issue
Due to known issue when there's `AndroidManifest.xml` in `app/App_Resources/Android`, there must be at least one nativescript plugin, which also has `AndroidManifest.xml` for merging.
I've used `nativescript-barcodescanner`. The issue will be fixed in `1.5.1` release of android runtime.
In case you have another plugin that has `AndroidManifest.xml`, there's no need to use `nativescript-barcodescanner`.
