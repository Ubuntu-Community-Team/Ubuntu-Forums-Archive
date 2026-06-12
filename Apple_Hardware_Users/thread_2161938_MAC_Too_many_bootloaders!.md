---
title: "MAC Too many bootloaders!"
date: 2013-07-12
forum: Apple Hardware Users
---

### Post by Donniedork0 on 2013-07-12
Okay so as you may have guessed i have multiple systems installed on my Macbook Pro, i currently have Mac OS X, Ubuntu 12.04 LTS, Backtrack 5R3, and Windows 7 installed. The problem im having is that i am trying to circumvent GRUB in general. My current set up is rEFInd efi shell, which allows me to choose which OS to boot at startup, the problem escalates from there, The Ubuntu GRUB loader timeout is set to 0 is working wonderfully, and when i selected windows 7 in rEFInd (before i installed backtrack 5) it would just boot windows 7 directly, but when i installed Backtrack 5 i am now getting a black GRUB screen when booting into windows and the timeout is 1 Second, so im having to mash the down key to get to the proper windows kernel. so what i want to know is how do i get my windows to boot properly from rEFInd without going into the grub loader. and also how can i rename the linux partitions in rEFInd? i kno this isnt an ubuntu question in particular. but you're the best at handling grub problems, so i figured i would start at the top! :P P.S. upon further investigation it appears as though my ubuntu's GRUB is bios emulation and my Backtrack 5 has an EFI GRUB...

Thanks to anyone who wasted time reading this, and to those who help and feel my pain!

---

### Post by oldfred on 2013-07-12
I am moving your thread to the Apple sub-forum. They may be the only one's that know Mac and rEFInd.
It was my understanding the new UEFI 2 versions did not work well with the somewhat older Mac UEFI which is between version one & two. But some have made it work.

       Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)

            Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

    
Info on rEFInd:
 Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards]("https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards")
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

