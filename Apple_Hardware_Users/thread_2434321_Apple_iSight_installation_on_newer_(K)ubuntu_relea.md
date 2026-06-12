---
title: "Apple iSight installation on newer (K)ubuntu releases"
date: 2020-01-03
forum: Apple Hardware Users
---

### Post by kle2 on 2020-01-03
I want to share here my experience in conjunction with installing an Apple iSight camera under **Kubuntu 18.04 LTS** running in _native EFI mode_ (dual-boot). In short, my iSight is working absolutely **PERFECTLY**! The tested system is an older (SSD, RAM, BT 4.0 and 802.11ac upgraded) Apple iMac aluminum computer running the most recent supported Mac OS X version **10.11 El Capitan**.  Here starts my first note, - more recent iSight Firmware Tools versions (like **1.6-2build1**) are absolutely able to extract the iSight firmware also on newer Mac OS versions. Certain website claim that this is NOT possible and it will fail on Mac OS X 10.8.6  Snow Leopard and newer. Well, according to my latest test this is no longer true, - I can confirm that it worked for me perfectly at OS X 10.11 El Capitan. So it seems that the following article should be updated: [https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight) [br]1[/br] [br]1[/br] So what were my exact steps?  [br]1[/br] [br]1[/br] 1. Locate the **exact path** of the "AppleUSBVideoSupport" file at the "Macintosh HD" volume. It is essential to get the correct path-name, otherwise it will fail. In my case, with (K)ubuntu user profile called "franz", the path was:  ```
/media/franz/Macintosh HD/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
``` Note, you have to **change** the name "franz" with the name of _yours_ (K)ubuntu user profile! [br]1[/br]  [br]1[/br] 2.  Download the iSight Firmware Tools with the following command and follow the installer instruction. As mentioned, it is fundamentally important to enter at the firmware extraction the correct path of the AppleUSBVideoSupport file.  ```
sudo apt-get install isight-firmware-tools
```   3. After that, a webcam app should be installed, - I decided me for the following one:  ```
sudo apt-get install cheese
``` The iSight webcam should be now fully working. Because my Kubuntu 18.04 LTS is running in native EFI mode, I haven't to power off the iMac and boot it up again. However, this seems to be necessary if Linux is running in Bios/CSM mode. I can confirm this for an even older white polycarbonate iMac model. The camera only worked after reboot into Mac OS X and running (once) the Photo Booth app. [br]1[/br] [br]1[/br] Note, - if the firmware extraction fails, you have to remove at first the entire iSight Firmware Tools package with the following command. After that, the package can be installed a second time.  ```
sudo apt-get --purge remove isight-firmware-tools
```  A special thanks goes to the following users at this archived post: [https://ubuntuforums.org/showthread.php?t=1389923](https://ubuntuforums.org/showthread.php?t=1389923)  [br]1[/br] [br]1[/br] Kind regards

---

### Post by sherylbrock on 2020-02-26
Thank you so much for this guide...
[COLOR=#3C4043][FONT=arial]
[COLOR=#ebece4]AppValley Download for iPhone, iPad - 2020. Get Tweaked (++) Apps and MOD Games. Free Spotify++ on your iOS device. No Jailbreak![/COLOR][/FONT][/COLOR]
[[COLOR=#3C4043][FONT=arial][COLOR=#ebece4]AppValley[/COLOR][/FONT][/COLOR]]("https://appvalley.one/")

---

