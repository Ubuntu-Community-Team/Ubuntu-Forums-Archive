---
title: "Formating external HDD"
date: 2011-05-28
forum: Any Other OS
---

### Post by capo1949 on 2011-05-28
Hi all,
I am trying to format an external HDD, when I right click the drive on the desktop and request format,type cmpatible with linux (ext4).I get

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=949CDADD9CDAB8C6 from /media/WD USB 2

I googled and found I need to use ntfs config tool from here
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
I used
graham@graham-laptop:~$ sudo fdisk -l | grep NTFS | awk '{print $1}'
/dev/sda1
/dev/sda2
 Now I have a problem in that it is sdc I want to format

graham@graham-laptop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3404a757

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        3486    27897871    7  HPFS/NTFS
/dev/sda3            9993       60802   408125441    5  Extended
/dev/sda4            3487        9992    52259445   83  Linux
/dev/sda5            9993       59347   396438528   83  Linux
/dev/sda6           59347       60802    11685888   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003212d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       28456   228570112   83  Linux
graham@graham-laptop:~$ 

Some help with this would be greatly appreciated

---

### Post by nemilar on 2011-05-28
Your best bet is probably to use the 'gparted' program to partition/format it.

---

### Post by capo1949 on 2011-07-21
Hi

I kicked this problem into the long grass, and now I have a problem with another drive.
I am trying to reformat a USB HDD that is formatted NTFS, using Gparted and a live CD of mint 10.
The problem that I am experiencing is that when I select sdb1 to reformat the option is greyed out. If I unmount it and try to select the format function, it seems to remount and the option is still greyed out. 
Some help would be appreciated

---

