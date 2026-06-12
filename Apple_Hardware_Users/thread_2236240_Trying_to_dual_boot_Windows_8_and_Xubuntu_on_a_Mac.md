---
title: "Trying to dual boot Windows 8 and Xubuntu on a MacBook"
date: 2014-07-25
forum: Apple Hardware Users
---

### Post by wint2 on 2014-07-25
Greetings, I have a MacBook Pro (11,1). I've installed Windows 8, and then I shrunk the partition and installed Xubuntu alongside it. I ran boot-repair to attempt to be able to boot into the Windows side of things and I selected the recommended settings. Unfortunately Windows is not listed in my grub menu and even Xubuntu won't load, it is stuck at the splash screen with the circle spinning. This is the log from my boot-repair attempt, if anyone has any insight I would be grateful for some help.[http://paste.ubuntu.com/7855909/](http://paste.ubuntu.com/7855909/)

---

### Post by oldfred on 2014-07-25
Moved to Apple sub-forum.

I do not know Mac.
But you are not showing any NTFS partition. If you used any auto install option and it does not correctly see an install it may just overwrite it. Always use Something else install option and choose which partition to use.

Does the new Windows 8 boot in UEFI mode or only in BIOS still as Apple still uses an older efi implementation that does not work easily with newer UEFI based systems. My understanding is that you can make Ubuntu work in UEFI mode.

I have older links, not sure any apply to Windows 8. But it uses fast boot or always on hibernation which creates many other issues as then other systems do not see it when hibernated.

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
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)
Boot Windows from Mac with UEFI. Long thread 2009 thru 2014 
[http://forums.macrumors.com/showthread.php?t=696523](http://forums.macrumors.com/showthread.php?t=696523)
Dual-boot OS X 10.8.4 / Ubuntu 12.04 LTS 64 bits on MacBookPro9,1 
[http://ubuntuforums.org/showthread.php?t=2167446](http://ubuntuforums.org/showthread.php?t=2167446)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)
Caution on UEFI boot Mac
[http://ubuntuforums.org/showthread.php?t=2012588](http://ubuntuforums.org/showthread.php?t=2012588)
Triple Boot MacbookPro (Lion, Win7, Ubuntu) Ubuntu in BIOS mode
[http://ubuntuforums.org/showthread.php?t=1908210](http://ubuntuforums.org/showthread.php?t=1908210)
New Haswell MacBook Air - several issues
[http://www.phoronix.com/scan.php?page=article&item=apple_mba2013_ubuntu&num=1](http://www.phoronix.com/scan.php?page=article&item=apple_mba2013_ubuntu&num=1)
NTFS on Mac
[https://discussions.apple.com/message/20943723#20943723](https://discussions.apple.com/message/20943723#20943723)

---

