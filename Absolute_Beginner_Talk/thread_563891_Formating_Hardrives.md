---
title: "Formating Hardrives"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Arukas on 2007-09-30
Hello, 

  I have a harddrive I want to format to FAT32 so windows and linux can both write to it.  However, XP conveniently don't have FAT32 option, what a surprise.

  I hate using the LiveCDs, they are flakey sometimes, and I don't have time for flakeyness.

 What I want to do, is format my second harddrive using Ubuntu.  I have fiesty fawn, if anyone needs to know.


-Arukas

---

### Post by atlfalcons866 on 2007-09-30
how big is the harddrive? if it is under 32Gb then you format is as fat32. I woldnt recommend fat32 though as it has 4GB file limit, fragments a lot, and it slows down as more files are added.

 You can use ntfs under ubuntu but i forget what the program is called. You can also use ext2 under windows if you use the IFS driver under windows. You can get it here [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by atlfalcons866 on 2007-09-30
also post your fdisk 

sudo fdisk -l

---

### Post by Arukas on 2007-09-30
Hello,

  I posted the fdisk at the end.  My second harddrive is 500 gigs.  I'd like both operating system to be able to write to the disk.  I would like to give Ubuntu the ability to write to it.   The drive is already in NTFS.  And so far, everything I have tried will not get ubuntu to write to the HDD.  



-Arukas


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19699   158232186    7  HPFS/NTFS
/dev/sda2           19700       38156   148255852+  83  Linux
/dev/sda3           38157       38913     6080602+   5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      969018   488385040+   7  HPFS/NTFS

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19929   160079661    c  W95 FAT32 (LBA)

---

### Post by Arukas on 2007-09-30
If getting XP to read a EXT partition, and it will read it fine, is there a way, I can format it in EXT without using a live CD?


-Arukas

---

### Post by Whiffle on 2007-09-30
[http://www.fs-driver.org](http://www.fs-driver.org)

I have all my data partitions formatted with ext3 and that driver will read it under XP.  Works good so far but I almost never use XP.  Should be able to format it under linux.  This has some relevant information i do believe:

[http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/](http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/)

---

### Post by atlfalcons866 on 2007-09-30
no you can only format ntfs and fat32 under windows but you can use gparted to format it.

---

### Post by vanadium on 2007-09-30
To perform the actual format, there are a few possibilities. (1) The easiest for you will be to use gparted (be carefull!!)

* Alt+F2, type "sudo gparted"
* In the right corner, find the drive where the partition you want to format resides
* If there are no partitions, you will need to create one. If it is there, right-click allows to format. If the partition is mounted (= in use), you need to Unmount it.

(2) With the command line, you can find out the name of the partition by looking it up in the output of fdisk -l. Eventually you need to unmount it, then you can format. Using /dev/sdb1 as an example:

sudo fdisk -l
sudo umount /dev/sdb1
sudo mkfs -t vfat /dev/sdb1

Indeed vfat guarantees compatibility, but as the other posts state, tehre are different options nowadays: use ext2 and use the ext2 driver under Windows or use ntfs and use ntfs-3g under Linux.

[Edit] I am not sure if gparted is installed by default on an Ubuntu system. If it is not there, install it first using System - Administration - Synaptic Package Manager

---

### Post by atlfalcons866 on 2007-09-30
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

