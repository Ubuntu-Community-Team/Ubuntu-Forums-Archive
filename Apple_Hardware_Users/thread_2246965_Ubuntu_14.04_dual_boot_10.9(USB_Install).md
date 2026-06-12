---
title: "Ubuntu 14.04 dual boot 10.9(USB Install)"
date: 2014-10-04
forum: Apple Hardware Users
---

### Post by izan2 on 2014-10-04
Hi everyone

Im new to the forum. Not very new to Linux but not a pro ;-)

Im trying to get the new 14.04  to load on my iMac 24" (7,1)

Any advice on how to if the SUPERDRIVE is not working anymore?

I've followed this thread:
[http://ubuntuforums.org/showthread.php?t=1261747&p=7926629#post7926629](http://ubuntuforums.org/showthread.php?t=1261747&p=7926629#post7926629)

Problem is the grub is designed for 9.04 and wont boot 14.04.
Maybe there is a new grub for what I need?

---

### Post by oldfred on 2014-10-04
Do not know Macs especially with all the versions:

 Fix for making bootable Ubuntu Live USB with persistence using Unetbootin on a Mac
[http://ubuntuforums.org/showthread.php?t=2174630](http://ubuntuforums.org/showthread.php?t=2174630)

But Ubuntu uses grub2 which can boot in BIOS or UEFI mode. But Macs use an older version of UEFI so the install in UEFI mode is not quite as easy. And Ubuntu will boot from gpt drives in either UEFI or BIOS mode if you have an efi partition for UEFI or a bios_grub for BIOS boot. 
Windows requires the hybrid MBR/gpt configuration which otherwise you want to avoid.


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
      
 Dual-boot OS X 10.8.4 / Ubuntu 12.04 LTS 64 bits on MacBookPro9,1 
[http://ubuntuforums.org/showthread.php?t=2167446](http://ubuntuforums.org/showthread.php?t=2167446)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)

---

### Post by este.el.paz on 2014-10-06
> **izan2 said:**
> Hi everyone

Any advice on how to if the SUPERDRIVE is not working anymore?

I've followed this thread:
[http://ubuntuforums.org/showthread.php?t=1261747&p=7926629#post7926629](http://ubuntuforums.org/showthread.php?t=1261747&p=7926629#post7926629)

Problem is the grub is designed for 9.04 and wont boot 14.04.
Maybe there is a new grub for what I need?

@izan:

What oldfred provided in terms of making a bootable USB would be your best option . . . I have yet to try using the USB option so I can't provide any insights on that.  But, in terms of that thread, that was from '09 . . . which is "old" . . . the suggestion to try "rEFIt" might be pointing in the right direction . . . but, now it would be "rEFInd" . . . that would be installed in the 10.9 volume . . . and **might** be helpful to boot the USB system.  I have a triple boot system on a MBPro . . . using rEFInd & GRUB2 ????  I didn't have to search around for some special GRUB, it's whatever the buntu installer uses . . . first try the install . . . if you have "free space" try using "install into largest free space" as your choice of installs . . . otherwise, you would need to manually partition the drive, providing a space flagged as "bios_grub" for GRUB, and then root/home, and then swap, etc.

---

