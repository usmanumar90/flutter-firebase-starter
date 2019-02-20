# mydiary


## Getting Started
Flutter Firebase Starter project is aimed for any one to quickly download and replace his/her firebase files as directed below and ready to do work instead of configuring the Firebase in Flutter especially for iOS there are much issues.

For quick start developing for Flutter Firebase project follow 1 to start from scratch to see each step how is it going follow 2.

#1
# How to run this Project on iOS and Android 

For iOS:
Open terminal at ios folder and run 'pod install' command and bear in mind dont open the XCode at this time once it is installed then open VSCode or whatever editor you are using and run the command for flutter
flutter packages get
once this is done, now you can run the application on iOS or Android

Remember to replace your Firebase file for iOS at location
ios/Runner/GoogleService-Info.plist
for Android replace at location
android/app/google-services.json

##Note: If you want to configure Firebase from start for your own project follow the guide given below for each step

#2

## How to Add Firebase for iOS in Flutter:

Google services use CocoaPods to install and manage dependencies. Open a terminal window and navigate to the location of the Xcode project for your app.

Create a Podfile if you don't have one:
pod init

Open your Podfile and add:
pod 'Firebase/Core'

Includes Analytics by default help_outline
Save the file and quit the XCode and then run:
pod install
This creates an .xcworkspace file for your app. Use this file for all future development on your application.

If you get some warnings like mentioned below:

[!] CocoaPods did not set the base configuration of your project because your project already has a custom config set. In order for CocoaPods integration to work at all, please either set the base configurations of the target `Runner` to `Pods/Target Support Files/Pods-Runner/Pods-Runner.profile.xcconfig` or include the `Pods/Target Support Files/Pods-Runner/Pods-Runner.profile.xcconfig` in your build configuration (`Flutter/Release.xcconfig`).

Then do the following process:

This issue can be solved as follow 

Go to Project Navigator
Select Project instead of Targets
Select Info
In Configurations, select each one, one at a time (Debug, ApplicationUnitTest, Release, etc.), and for each target within said configuration, set configuration to None.
Make certain that Based on Configuration File reads 0 Configurations Set or No Configurations Set for each configuration. That is the necessary part.
Quit xcode
run the command again:
pod install


If you get issue of some like 'PhaseScriptExecution failed with a nonzero exit code' or 'xcode_backend.sh No such file or directory' then do the following:

Go to Project Navigator
Select Target and add User-Defined Setting with key name **FLUTTER_ROOT** with the value of your flutter SDK location.
Clean the XCode and Build again Flutter will start working with XCode with Firebase integrated.

Add the GoogleService-Info.plist from Firebase into your project

Now add the Firebase settings in AppDelegate.swift file:

Import the Firebase module in your UIApplicationDelegate:
SWIFTOBJECTIVE-C
import Firebase
Configure a FirebaseApp shared instance, typically in your application's application:didFinishLaunchingWithOptions: method:
SWIFTOBJECTIVE-C
// Use Firebase library to configure APIs
FirebaseApp.configure()

## How to Add Firebase for Android in Flutter:

The Google services plugin for Gradle loads the google-services.json file that you just downloaded from Firebase account. Modify your build.gradle files to use the plugin.

Project-level build.gradle (<project>/build.gradle):

buildscript {
  dependencies {
    // Add this line
    classpath 'com.google.gms:google-services:4.0.1'
  }
}

App-level build.gradle (<project>/<app-module>/build.gradle):
dependencies {
  // Add this line
  implementation 'com.google.firebase:firebase-core:16.0.1'
}
...
// Add to the bottom of the file
apply plugin: 'com.google.gms.google-services'

Includes Analytics by default help_outline
Finally, press 'Sync now' in the bar that appears in the IDE:

###Note: For Android keep remember to use the latest versions of firebase packages.

