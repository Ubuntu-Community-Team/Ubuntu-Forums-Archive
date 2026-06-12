---
title: "where is the partition gone!!!!"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-06-14
well lil bit of background before i tell you the problem.

i have hdd1 40gb/5 partitions and hdd 160gb/4 partitions. i have windows xp installed in one partition and ubuntu installed in the other(the 2 being in the 2 different disks). Ubuntu was showing all the drives after the installation was complete. only a few days back i had to quick format one of the partitions....and then on ubuntu is not showing that partition at all!.. infact at boot up it shows mounting local filesystem as fail! XP shows it well and i can use it happily there! what to i do!!!:confused:

---

### Post by vanadium on 2007-06-14
This indicates that the entry in /etc/fstab is not anymore correct, probably because you have formatted to another file system. Post the output of sudo fdisk -l and of your /etc/fstab here if you want us to be able to point to the error.

---

### Post by badguyanil on 2007-06-14
> **vanadium said:**
> This indicates that the entry in /etc/fstab is not anymore correct, probably because you have formatted to another file system. Post the output of sudo fdisk -l and of your /etc/fstab here if you want us to be able to point to the error.

well the file system was FAT32 and is FAT 32.Anyways i am not at home right now will surely post the same today evening.Thanks for the help! stll is there i can try out till then!

---

### Post by badguyanil on 2007-06-14
Well here is what fdisk gives me...........

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    c  W95 FAT32 (LBA)
/dev/sda2            4866       19457   117210240    f  W95 Ext'd (LBA)
/dev/sda5            4866        9730    39078081    b  W95 FAT32
/dev/sda6            9731       14595    39078081    b  W95 FAT32
/dev/sda7           14596       19457    39053983+   b  W95 FAT32

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         973     7815591    b  W95 FAT32
/dev/sdb2             974        4865    31262490    f  W95 Ext'd (LBA)
/dev/sdb5             974        1937     7743298+   b  W95 FAT32
**[COLOR="Red"]/dev/sdb6            1938        2902     7751331    b  W95 FAT32[/COLOR]**
/dev/sdb7            2903        3892     7952143+   b  W95 FAT32
/dev/sdb8            3893        3954      497983+  82  Linux swap / Solaris
/dev/sdb9            3955        4865     7317576   83  Linux


This is the drive that does not mount automatically. But after boot up i can right click on the drive icon and mount it.
and the below are the contents of my /etc/fstab file...
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb9
UUID=9cc6710e-ffe0-4028-9b29-770361f33bac /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=261D-1BE8  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=7414-234B  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=78BC-B50D  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=7D64-8A86  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=8402-F5AD  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=340C-F425  /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
[COLOR="Red"][B]# /dev/sdb6
UUID=3C35-17E4  /media/sdb6     vfat    defaults,utf8,umask=007,gid=46 0       1[/B][/COLOR]
# /dev/sdb7
UUID=1B42-17E8  /media/sdb7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb8
UUID=687a1f5f-3696-46b8-acfe-e9149569558a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

and the error at bootup says uuid--3C35-17E4 cannot be mounted and fail msg!
...help!!!!!!!!

---

### Post by badguyanil on 2007-06-15
any subbestions!

---

