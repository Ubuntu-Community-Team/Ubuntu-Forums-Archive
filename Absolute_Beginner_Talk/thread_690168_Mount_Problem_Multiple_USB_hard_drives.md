---
title: "Mount Problem Multiple USB hard drives"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by fcorourke on 2008-02-07
Hi, I am running 7.10 Gutsy 32-bit as I got tired of arranging things on the 64 bit version for my AMD 3800 Dual Core. I am pasting disk info at the end. The main problem is I disliked very much Windows XP and system locks & want to work with Ubuntu 97% of the time or more --  I use & need Publisher sometimes. The improper shutdown, drives me crazy. I installed Ubuntu to stop problems but tcan never seem to get all my disks online at one time. Is it possible to mount all drives -- all the time? I have reinstalled Windows XP on an alternate drive & when I need Windows -- to copy between drives etc, I shut down & unplug Linux drive & boot up. In Windows, I can see all my drives & access them. I am thinking of purchasing a "Safe Shutdown" program for my USB drives. as Windows will not always release a drive. THIS is one problem, if you have a lock up in Windows -- that means only 1 or 2 USB drives seen if you start Ubuntu -- Must restart Windows & then SUT DOWn usb safely. This is a majot stumbling point for me.  WHAT can I do in Windows to get Linux to see all my drives? Once I reboot into Windows -- I just as well stay for a while & even with safely removing USB drives -- "according to Windows - drive is not there" -- not all drives present.  -- I am tired -- I can always see everything if I boot into the live CD, but not do antyhing with what I see.

         Fred  :(

fred@fred-desktop:~$ fdisk -l

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x690e25bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28c82b84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f3ba0f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *       31116       31302     1502077+   c  W95 FAT32 (LBA)
/dev/sdd2               1       31115   249931206    c  W95 FAT32 (LBA)
/dev/sdd3           31303       60801   236950717+   c  W95 FAT32 (LBA)

Partition table entries are not in disk order

Disk /dev/sdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17e1dd8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       14593   117218241    c  W95 FAT32 (LBA)
fred@fred-desktop:~$ 


.

---

### Post by fcorourke on 2008-02-07
I can  see all but one drive -- the one with all the data I would like. 120 Gig fat32 -- also only some drives have their name -- that I can live with forever

     fred

---

