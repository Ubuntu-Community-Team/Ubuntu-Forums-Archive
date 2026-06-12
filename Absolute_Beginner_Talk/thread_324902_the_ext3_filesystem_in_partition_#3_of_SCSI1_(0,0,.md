---
title: "the ext3 filesystem in partition #3 of SCSI1 (0,0,0) (sda) failed"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by techbuddy on 2006-12-24
Hello all,

this is my 12th hour trying to install ubuntu 6.10.
So this is my environment
Dell laptop ( i386 arch )  - internal HDD of 60 GB
one 250 GB external USB

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         600     4819468+  83  Linux
/dev/sda2             601        1200     4819500   83  Linux
/dev/sda3            1201        1800     4819500   83  Linux
/dev/sda4            1801       30401   229737532+   f  W95 Ext'd (LBA)
/dev/sda5            1801        2400     4819468+   7  HPFS/NTFS
/dev/sda6            2401        2662     2104483+  82  Linux swap / Solaris
/dev/sda7            2663        3000     2714953+   7  HPFS/NTFS
/dev/sda8            3001        5000    16064968+  83  Linux
/dev/sda9            5001       10000    40162468+  83  Linux
/dev/sda10          10001       15000    40162468+   b  W95 FAT32
/dev/sda11          15001       20261    42258951    b  W95 FAT32
/dev/sda12          20262       25998    46082421    b  W95 FAT32
/dev/sda13          25999       30401    35367066    b  W95 FAT32

i am trying to install ubuntu on any of the linux partitions and in the same time saving the ntfs/fat32 partitions as i have datas in them.
Q1 . why do i have to reformat when i already have a ext3 on my system  ( through partition magic  
Q2.  i select manually edit partition and choose the /dev/sda . I select /dev/sda1 for installation and /dev/sda6 for swap. The only two entry will be / on  /dev/sda1 and swap on /dev/sda6 and i click forward/install(?) . at 15% it always breaks and throws the 
error :
The ext3 file system in partition #3 of SCSI1 (0,0,0) (sda) failed.

 As you will see this time i checked with /dev/sda3. I have checked with other linux partitions too. I also tried to remove the lba flag but nothing seems to work !! 
Any help ?

Tutu

---

