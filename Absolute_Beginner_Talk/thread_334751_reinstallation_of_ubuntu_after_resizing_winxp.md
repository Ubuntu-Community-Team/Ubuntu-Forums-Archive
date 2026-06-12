---
title: "reinstallation of ubuntu after resizing winxp"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by beafer on 2007-01-09
I had my computer (Sony VAIO-SZ3HP/B) working fine with dual-boot Winxp and Ubuntu 6.06 until I decided to resize the Windows partition since it was too big (40 GB). In order to resize the windows partition I started to reinstall Ubuntu again and change the size of the partitions with the gParted program that comes with the Ubuntu installation CD. So, I resized the windows partition and gave 20 GB to linux,  the final partition table looks like:

Device Boot          Size                  Id        System 
/dev/sda1          7.92   GB            12       Compaq diagnostics   
/dev/sda2          23.22 GB             7         HPFS/NTFS 
/dev/sda3         10.00  GB            83        Linux (ext3)
/dev/sda4         55.90  GB              5        Extended
  /dev/sda5          1.00 GB            82      linux swap  /solaris
  /dev/sda6        30.72 GB            83      linux
  /dev/sda7        24.16 GB             b       W95  fat32

But when trying to reinstall ubuntu installation aborts with the following message:

 Creating ext3 filesystem for /  in part#3 of SCSl1(0,0,0) (sda)
......Error: invalid file system for this mount point 

Does anyone knows what should I do first to fix the problem?  
Thanks in advance for any help.

---

