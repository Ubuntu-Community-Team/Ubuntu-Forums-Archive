---
title: "ssh ramdisk on iphone with ubuntu jelly"
date: 2022-11-29
forum: Apple Hardware Users
---

### Post by kronosxtitans on 2022-11-29
i managed to delet it but it was back, so does this mean i must give read write permissions to the directory in root

```

localhost:/var root# /mnt2
-sh: /mnt2: is a directory
localhost:/var root# mount /var
mount_apfs: volume could not be mounted: Resource busy
mount: /private/var failed with 75
localhost:/var root# /var h
-sh: /var: is a directory
localhost:/var root# /var is mounted to /mnt2
-sh: /var: is a directory
localhost:/var root# ls
log    logs    root    tmp
localhost:/var root# ls [flags] [directory]
ls: [directory]: No such file or directory
ls: [flags]: No such file or directory
localhost:/var root# ls /var
log    logs    root    tmp
localhost:/var root# ls /mnt2
.DocumentRevisions-V100    datamigrator        msgs
.fseventsd        db            networkd
.overprovisioning_file    dirs_cleaner        preferences
Keychains        empty            protected
Managed Preferences    folders            root
MobileAsset        hardware        run
MobileDevice        installd        select
MobileSoftwareUpdate    keybags            tmp
audit            log            vm
buddy            logs            wireless
containers        mobile
localhost:/var root# ls mobile
ls: mobile: No such file or directory
localhost:/var root# /mobile
-sh: /mobile: No such file or directory
localhost:/var root# ls /mobile cd
ls: /mobile: No such file or directory
ls: cd: No such file or directory
localhost:/var root# cd mobile
-sh: cd: mobile: No such file or directory
localhost:/var root# ls/
-sh: ls/: No such file or directory
localhost:/var root# ls /
System    dev    mnt1    mnt3    mnt5    mnt7    mnt9    sbin    var
bin    etc    mnt2    mnt4    mnt6    mnt8    private    usr
localhost:/var root# /mnt2
-sh: /mnt2: is a directory
localhost:/var root# ls mnt2
ls: mnt2: No such file or directory
localhost:/var root# ls /mnt2
.DocumentRevisions-V100    datamigrator        msgs
.fseventsd        db            networkd
.overprovisioning_file    dirs_cleaner        preferences
Keychains        empty            protected
Managed Preferences    folders            root
MobileAsset        hardware        run
MobileDevice        installd        select
MobileSoftwareUpdate    keybags            tmp
audit            log            vm
buddy            logs            wireless
containers        mobile
localhost:/var root# ls..
-sh: ls..: command not found
localhost:/var root# ls../..
-sh: ls../..: No such file or directory
localhost:/var root# ls~
-sh: ls~: command not found
localhost:/var root# ls ~
localhost:/var root# ls /mnt2
.DocumentRevisions-V100    datamigrator        msgs
.fseventsd        db            networkd
.overprovisioning_file    dirs_cleaner        preferences
Keychains        empty            protected
Managed Preferences    folders            root
MobileAsset        hardware        run
MobileDevice        installd        select
MobileSoftwareUpdate    keybags            tmp
audit            log            vm
buddy            logs            wireless
containers        mobile
localhost:/var root# ls *
log:

logs:
ramrod        restored

root:

tmp:
localhost:/var root# ls -r
tmp    root    logs    log
localhost:/var root# ls/mnt2
-sh: ls/mnt2: No such file or directory
localhost:/var root# ls mnt2
ls: mnt2: No such file or directory
localhost:/var root# ls -a
.    ..    log    logs    root    tmp
localhost:/var root# man ls
-sh: man: command not found
localhost:/var root# /var
-sh: /var: is a directory
localhost:/var root# ls /mnt2
.DocumentRevisions-V100    datamigrator        msgs
.fseventsd        db            networkd
.overprovisioning_file    dirs_cleaner        preferences
Keychains        empty            protected
Managed Preferences    folders            root
MobileAsset        hardware        run
MobileDevice        installd        select
MobileSoftwareUpdate    keybags            tmp
audit            log            vm
buddy            logs            wireless
containers        mobile
localhost:/var root# /mobile dir
-sh: /mobile: No such file or directory
localhost:/var root# cd mobile
-sh: cd: mobile: No such file or directory
localhost:/var root# /containers
-sh: /containers: No such file or directory
localhost:/var root# ls / containers
ls: containers: No such file or directory
/:
System    dev    mnt1    mnt3    mnt5    mnt7    mnt9    sbin    var
bin    etc    mnt2    mnt4    mnt6    mnt8    private    usr
localhost:/var root# ls /mnt2
.DocumentRevisions-V100    datamigrator        msgs
.fseventsd        db            networkd
.overprovisioning_file    dirs_cleaner        preferences
Keychains        empty            protected
Managed Preferences    folders            root
MobileAsset        hardware        run
MobileDevice        installd        select
MobileSoftwareUpdate    keybags            tmp
audit            log            vm
buddy            logs            wireless
containers        mobile
localhost:/var root# ls mnt1
ls: mnt1: No such file or directory
localhost:/var root# ls /mnt1
.ba        Developer    cores        sbin
.file        Library        dev        tmp
.mb        System        etc        usr
Applications    bin        private        var
localhost:/var root# ls /applications
ls: /applications: No such file or directory
localhost:/var root# cd /applications
-sh: cd: /applications: No such file or directory
localhost:/var root# ls /mnt1/application
ls: /mnt1/application: No such file or directory
localhost:/var root# ls /mnt1/application
ls: /mnt1/application: No such file or directory
localhost:/var root# /var/mnt1/application
-sh: /var/mnt1/application: No such file or directory
localhost:/var root# ls /mnt1
.ba        Developer    cores        sbin
.file        Library        dev        tmp
.mb        System        etc        usr
Applications    bin        private        var
localhost:/var root# cd application
-sh: cd: application: No such file or directory
localhost:/var root# cd /applications
-sh: cd: /applications: No such file or directory
localhost:/var root# ls /mnt1
.ba        Developer    cores        sbin
.file        Library        dev        tmp
.mb        System        etc        usr
Applications    bin        private        var
localhost:/var root# cd applications
-sh: cd: applications: No such file or directory
localhost:/var root# pwd
/var
localhost:/var root# ls /mnt1
.ba        Developer    cores        sbin
.file        Library        dev        tmp
.mb        System        etc        usr
Applications    bin        private        var
localhost:/var root# gnome-open
-sh: gnome-open: command not found
localhost:/var root# gnome - open
-sh: gnome: command not found
localhost:/var root# ls /mnt1
.ba        Developer    cores        sbin
.file        Library        dev        tmp
.mb        System        etc        usr
Applications    bin        private        var
localhost:/var root# open folder
-sh: open: command not found
localhost:/var root# ls /mnt1
.ba        Developer    cores        sbin
.file        Library        dev        tmp
.mb        System        etc        usr
Applications    bin        private        var
localhost:/var root# cd /var/mnt1/Applications
-sh: cd: /var/mnt1/Applications: No such file or directory
localhost:/var root# list /mnt1
-sh: list: command not found
localhost:/var root# ls /mnt1
.ba        Developer    cores        sbin
.file        Library        dev        tmp
.mb        System        etc        usr
Applications    bin        private        var
localhost:/var root# cd
localhost:~ root# ls /mnt1
.ba        Developer    cores        sbin
.file        Library        dev        tmp
.mb        System        etc        usr
Applications    bin        private        var
localhost:~ root# mount applications
mount: applications: invalid special file or file system.
localhost:~ root# pwd
/var/root
localhost:~ root# pwd /applications
/var/root
localhost:~ root# ls /applications
ls: /applications: No such file or directory
localhost:~ root# ls /mnt1
.ba        Developer    cores        sbin
.file        Library        dev        tmp
.mb        System        etc        usr
Applications    bin        private        var
localhost:~ root# cd A
-sh: cd: A: No such file or directory
localhost:~ root# cd A 
-sh: cd: A: No such file or directory
localhost:~ root# ls  
localhost:~ root# 
localhost:~ root# 
localhost:~ root# cd /mnt1
localhost:/mnt1 root# pwd
/mnt1
localhost:/mnt1 root# ls -a
.        .mb        System        etc        usr
..        Applications    bin        private        var
.ba        Developer    cores        sbin
.file        Library        dev        tmp
localhost:/mnt1 root# cd Applications/
localhost:/mnt1/Applications root# ls -a
.
..
AAUIViewService.app
AMSEngagementViewService.app
AXUIViewService.app
AccountAuthenticationDialog.app
ActivityMessagesApp.app
AnimojiStickers.app
AppSSOUIService.app
AppSettings.app
AppStore.app
Apple TV Remote.app
AskPermissionUI.app
AuthKitUIService.app
AuthenticationServicesUI.app
BarcodeScanner.app
BusinessChatViewService.app
BusinessExtensionsWrapper.app
CTCarrierSpaceAuth.app
CTKUIService.app
CTNotifyUIService.app
Camera.app
CarPlaySettings.app
CarPlaySplashScreen.app
CarPlayWallpaper.app
CheckerBoard.app
ClipViewService.app
CompanionAuthViewService.app
CompassCalibrationViewService.app
ContactlessReaderUIService.app
CoreAuthUI.app
CredentialSharingUIViewService.app
DDActionsService.app
DataActivation.app
DemoApp.app
Diagnostics.app
DiagnosticsService.app
DisplayCal.app
ExposureNotificationRemoteViewService.app
FMDMagSafeSetupRemoteUI.app
FaceTimeLinkTrampoline.app
Family.app
FamilyControlsAuthenticationUI.app
Feedback Assistant iOS.app
FieldTest.app
FindMy.app
FindMyExtensionContainer.app
FontInstallViewService.app
FunCameraEmojiStickers.app
FunCameraShapes.app
FunCameraText.app
GameCenterRemoteAlert.app
GameCenterUIService.app
GameCenterWidgets.app
HDSViewService.app
HashtagImages.app
Health.app
HealthENBuddy.app
HealthENLauncher.app
HealthPrivacyService.app
HomeCaptiveViewService.app
HomeControlService.app
HomeUIService.app
InCallService.app
MBHelperApp.app
MTLReplayer.app
MailCompositionService.app
MessagesViewService.app
MobilePhone.app
MobileSMS.app
MobileSafari.app
MobileSlideShow.app
MobileTimer.app
MusicRecognition.app
MusicUIService.app
PaperBoard.app
Passbook.app
PassbookBanner.app
PassbookSecureUIService.app
PassbookUIService.app
PeopleViewService.app
PhotosUIService.app
PreBoard.app
Preferences.app
Print Center.app
ProximityReaderUIService.app
RecoverDeviceUI.app
RemotePaymentPassActionsService.app
RemoteiCloudQuotaUI.app
SIMSetupUIService.app
SLYahooAuth.app
SMS Filter.app
SafariViewService.app
Screen Time.app
ScreenSharingViewService.app
ScreenTimeUnlock.app
ScreenshotServicesService.app
Setup.app
SharedWebCredentialViewService.app
SharingViewService.app
ShortcutsViewService.app
Sidecar.app
Siri.app
SleepLockScreen.app
SleepWidgetContainer.app
SoftwareUpdateUIService.app
Spotlight.app
StoreDemoViewService.app
StoreKitUIService.app
SubcredentialUIService.app
TVAccessViewService.app
TVSetupUIService.app
TrustMe.app
Utilities
VideoSubscriberAccountViewService.app
Web.app
WebContentAnalysisUI.app
WebSheet.app
Xcode Previews.app
iCloud.app
iMessageAppsViewService.app
icq.app
localhost:/mnt1/Applications root# rm setup.app                                
rm: setup.app: No such file or directory
localhost:/mnt1/Applications root# ls -larth setup.app
ls: setup.app: No such file or directory
localhost:/mnt1/Applications root# rm Setup.app
rm: Setup.app: is a directory
localhost:/mnt1/Applications root# rm Setup.app
rm: Setup.app: is a directory
                                                                                                                                                      localhost:/mnt1/Applications root# rm -r Setup.app                                                                                                   
localhost:/mnt1/Applications root# ls Setup.app
ls: Setup.app: No such file or directory
localhost:/mnt1/Applications root# reboot
localhost:/mnt1/Applications root# Connection to localhost closed by remote host.
Connection to localhost closed.
```

---

### Post by QIII on 2022-11-29
Moved to Apple Hardware Users

---

### Post by kronosxtitans on 2022-11-29
i am confused ..my entire post was deleted.I think i messed with the advance setting in this forum.Anyway i wanted to delete the setup .app file but it was still there when the device booted

---

### Post by QIII on 2022-11-29
Your post was not deleted, it was moved.

You have also removed the edits I made to contain your terminal output in code tags.  Please do not undo Staff edits.

---

### Post by TheFu on 2022-11-30
> **kronosxtitans said:**
> i am confused ..my entire post was deleted.I think i messed with the advance setting in this forum.Anyway i wanted to delete the setup .app file but it was still there when the device booted

I don't see what the output has to do with deleting a file?  90% of the post is non-sequitur stuff ... I can only assume it was meant to confuse us, for some reason.

```
# rm Setup.app
rm: Setup.app: is a directory
```
We cannot delete a directory with a simple 'rm' command.  'rmdir' is the command, but it only works if the directory is empty.
For non-empty directories, we have to delete everything in it and the directory. Try:
```
rm   -rf    /mnt1/Applications/Setup.app
```

If that doesn't work, show the command and the exact output wrapped in forum code tags, please.  We don't need 500 lines of junk. For that, I'd expect 3 lines if there is any error and nothing if it worked.

No clue what an iPhone or ssh have to do with this either.  They don't, just for clarity.

Seems that a little basic Unix/Linux knowledge is needed.  Here's a book that I've used in classes to help beginners learn this stuff.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Work through the first 120-ish pages to gain basic knowledge that the 90% of the output above seems to display.  All Unix-like OSes have skills that build on prior skills.  It is very difficult to jump into the middle of running commands without some basic understanding of the OS first and some of the basic commands.
For example, use 'ls -F' to have the system show directories different from files and different from symbolic links.  Basic, but important stuff.

---

