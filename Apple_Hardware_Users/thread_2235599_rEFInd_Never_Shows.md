---
title: "rEFInd Never Shows"
date: 2014-07-22
forum: Apple Hardware Users
---

### Post by Merik on 2014-07-22
Hey everyone!

I successfully installed Ubuntu on a partition, although now I can't boot into it. I've tried installing rEFInd, but every time I reboot it never shows up and just boots into Mac OS X.

I'm using OS X 10.9.4 with FileVault.

[IMG]https://dm2301files.storage.live.com/y2mcpuaytpa_m3vkNoljvThhrRtPs9qnxj8UXONfzfnHk8jCLZXyBSIWTYeCetc8RNdBztN0lP13By_v1NRYNXSOU8-Jkj6RdphTVnbaN9yqis/Screen%20Shot%202014-07-21%20at%2010.48.15%20PM.png.jpg?psid=1[/IMG]

disk0s4 - SWAP
disk0s5 - Ubuntu

---

### Post by oldfred on 2014-07-23
Moved to Apple subforum.
Please attach screen shots with paperclip icon in advanced editor, not in line.

I do not know if any of these older threads have any suggestions or not. 
I do not have nor know about Mac.

       [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[URL="http://www.rodsbooks.com/ubuntu-efi/index.html"]http://www.rodsbooks.com/ubuntu-efi/index.html

[/URL]
 Dual-boot OS X 10.8.4 / Ubuntu 12.04 LTS 64 bits on MacBookPro9,1 
[http://ubuntuforums.org/showthread.php?t=2167446](http://ubuntuforums.org/showthread.php?t=2167446)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)
Caution on UEFI boot Mac
[http://ubuntuforums.org/showthread.php?t=2012588](http://ubuntuforums.org/showthread.php?t=2012588)

[URL="http://www.rodsbooks.com/ubuntu-efi/index.html"]
[/URL]

---

### Post by este.el.paz on 2014-07-24
@Merik:

Should be that the links olfred has provided should help to get you going . . . it depends on where you have rEFInd installed how it will "show up" . . . if it's installed in front of OSX, then it should show up on reboot . . . so, first question, where did you install rEFInd?  And, second question, did you create a GRUB partition of about 10MB and labeled/flagged as "bios_grub" or something like that . . . and the "boot" partition needs to be "flagged" as "/" . . . unless you used "automatic" install?  Then after install you need to shut the unit down and restart fresh . . . to get rEFInd to show . . . .

Good luck,

e.e.p.

---

