---
title: "Grub not configuring correctly for multiple Ubuntu installations"
date: 2014-08-14
forum: Apple Hardware Users
---

### Post by mike-g2 on 2014-08-14
Oy!  I have spent all day trying to solve this problem and it's only got worse!

Background: MacPro3,1 with a separate HDD for OS's.  
No Mac OS, but multiple versions of Ubuntu (14.04.1 -fresh install, 14.04.1 upgrade from 12.04.5, and 12.04.5 for safety).

Problem #1) Mac will no longer boot from CD ROM.

Problem #2) Grub configuration is screwed up such that the UUIDs in the grub.cfg for 14.04.1 upgrade and 12.04.5 are really for the 14.04.1 fresh installation.  I've run grub-mkconfig multiple times to no avail.

Additional information: I've got boot-repair installed, but don't know how to configure it correctly (and not even sure if I should use it).  The output from it can be found at [http://paste.ubuntu.com/8049643/](http://paste.ubuntu.com/8049643/)

If someone could help me solve these problems, I'd appreciate it.

Mike

---

### Post by oldfred on 2014-08-14
I do not know Mac, but see a couple of things right off.
You have two efi partitions. Even if UEFI allows two, current system can only have one per hard drive or device. So sda1 as the FAT32 partition should be the efi partition. It cannot be a Linux formatted partition.

You also show bios_grub and grub installed to gpt's protective MBR. Generally UEFI boot works better with Mac as I understand it.
And you seem to have the hybrid MBR(msdos) and gpt partition table. That is required for Windows as it only boots with BIOS & MBR, but Ubuntu boots with UEFI.
       [URL="http://www.rodsbooks.com/gdisk/hybrid.html"]http://www.rodsbooks.com/gdisk/hybrid.html

[/URL]
 [URL="http://www.rodsbooks.com/gdisk/hybrid.html"]https://help.ubuntu.com/community/MacBookPro
      [/URL]
 Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
      
 [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
           
 [http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)
    
With 14.04 it should be even easier.

 Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
      
  MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)

 New Haswell MacBook Air - several issues
[http://www.phoronix.com/scan.php?page=article&item=apple_mba2013_ubuntu&num=1](http://www.phoronix.com/scan.php?page=article&item=apple_mba2013_ubuntu&num=1)
      
 Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)

    


 
    


 
    [URL="http://www.rodsbooks.com/gdisk/hybrid.html"]
[/URL]

---

### Post by mike-g2 on 2014-08-17
Thanks for the references. I'd seen some of them before and can only make sense of part of them.  I think the main source of my problem was the new install I did used grub-efi and the older installs used grub-pc.  Replacing grub-efi with grub-pc and then doing grub-mkconfig now allows me to boot the other installations.

---

