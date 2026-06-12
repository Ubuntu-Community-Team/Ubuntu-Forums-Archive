---
title: "sudo fdisk -l and using my external harddrive"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by redtendoned on 2007-07-15
I looked around the forum for a couple of hours to see what I could figure out on my own and it is now time to ask for your help. I have an external hard drive which contains all my classwork/music/and videos. It is a Seagate 80gb. Can someone explain to me how to access the files on my external?

chris@chris-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    c  W95 FAT32 (LBA)
chris@chris-laptop:~$

---

### Post by redtendoned on 2007-07-15
I suppose I should add....

The external hard drive has not been mounted. I was looking all around the forums looking for a how to but there was nothing really helpful too me. Lots of the how to's seemed directed towards individuals who had already mounted yet still had problems seeing/writing to their drives.

Ubuntu 7.04 is running perfectly on my laptop, and I've got everything just how I'd like it. My last questions are where are my drives? How do I access my 60 gb internal and my 80 gb external? The only things currently visible in Places -> Computer is CD-RW/DVD-ROM Drive and Filesystem

Sorry for being so ignorant, but can someone hold my hand for a second?! :confused: :o

---

