---
title: "Dualboot"
date: 2016-01-27
forum: Apple Hardware Users
---

### Post by dellboy56 on 2016-01-27
Hello guys today im trying to dualboot windows 10 and ubuntu my setup is a macbook pro 2010 running windows 10 i wiped os x etc off it and put only windows 10 on there now i would like to dualboot ubuntu i made a cd with windows and installed as a 32bit no efi then i burned a cd image of ubuntu 64 bit and i booted it without efi and it comes up with no operating systems detcted im never dualbooted before and im really stuck for help could you please provide me what to do thank you:)

---

### Post by oldfred on 2016-01-27
Moved to Apple sub-forum.

You need to install in UEFI boot mode.
       [http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)

   EFI partitions: Also some info on efi partition on a Mac.
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)
With 15.10
The amd64 (Intel x86 64bit) images specifically targeted at Apple hardware (amd64+mac) are no longer produced. 
[http://mattjanik.ca/blog/2015/10/01/refind-on-el-capitan/](http://mattjanik.ca/blog/2015/10/01/refind-on-el-capitan/)
[http://ubuntuforums.org/showthread.php?t=2297148](http://ubuntuforums.org/showthread.php?t=2297148)

   [http://ubuntuforums.org/showthread.php?t=2289225&p=13355890#post13355890](http://ubuntuforums.org/showthread.php?t=2289225&p=13355890#post13355890)

---

### Post by dellboy56 on 2016-01-27
I dont understand as you can see i dont have os x anymore on my mac i wiped it gone so im not surr why you would link me refind about that i have replaced [OSX] With [windows10] and i would like to dualboot so why would you link me that and a bootable usb when i installed windows 10 in 32bit format [NO EFI] but then i tried to install ubuntu 64bit 14.04 on it aswell just tells me no os found

---

### Post by oldfred on 2016-01-28
I do not know Mac, but your Mac hardware controls many of the ways you install. And UEFI is only 64 bit. Since hardware is 64bit, you are reducing its capability with 32 bit installs.

And most suggest only using UEFI on a Mac and keep OSX as you can only do some maintenance on system with it.
If you installed Windows in BIOS boot mode then you converted drive to MBR, but Macs are gpt with UEFI. You may then have a hybrid disk but have to use Mac tools to keep MBR & gpt in sync.

       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

Some more older threads:

 Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)


If you really want BIOS, I found this older thread.

 Triple Boot MacbookPro (Lion, Win7, Ubuntu) Ubuntu in BIOS mode
[http://ubuntuforums.org/showthread.php?t=1908210](http://ubuntuforums.org/showthread.php?t=1908210)

---

