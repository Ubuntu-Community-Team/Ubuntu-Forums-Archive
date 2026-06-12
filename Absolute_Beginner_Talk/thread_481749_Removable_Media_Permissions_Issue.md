---
title: "Removable Media Permissions Issue"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Dxh on 2007-06-22
I have most of my larger files and games on an external harddrive, which caused no problems on Ubuntu 6.10, but when I updated to 7.04, it never automounts at boot, even though its listed correctly in mtab and fstab, and everytime I manually boot it from terminal, it automatically sets it up as read-only, and no matter what I do, I can't get it to change those permissions. 

The issue is merely an annoyance until I try to run wine. When a program tries to run from the harddrive under normal user permissions, I get accessability errors. When I run it under sudo, wine crashes for some reason. Programs running off of my main HD run fine.

Any help would be greatly appreciated.

---

### Post by Najand on 2007-06-22
Can you give me the following information?
1. Is the filesystem of your Ext. HD NTFS?
2. Can you post the output of "sudo fdisk -l"?
3. Can you post your /etc/fstab file?

---

### Post by Dxh on 2007-06-22
1) Its fat32, vfat, or whatever you want to call it.
2)
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4281    34387101   83  Linux
/dev/sda2   *        4282        9327    40531995   83  Linux
/dev/sda3            9458        9729     2184840   82  Linux swap / Solaris
/dev/sda4            9328        9457     1044225    5  Extended
/dev/sda5            9328        9457     1044193+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    c  W95 FAT32 (LBA)

sdb is the external.

3)
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ff1ebb52-ad1f-4a64-9823-42fdb5541a56 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=65d69b9f-e68d-4d72-ad94-c13e68c216dd /media/hda2     ext3    defaults        0       2
# /dev/hda3
UUID=4577e2e9-6675-4b44-9766-b1d21ca9baf3 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

