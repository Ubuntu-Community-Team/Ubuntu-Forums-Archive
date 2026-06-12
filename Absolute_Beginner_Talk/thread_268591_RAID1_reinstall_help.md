---
title: "RAID1 reinstall help"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by michaelmj on 2006-09-30
I am a noobie and need some help please. I have just installed Dapper Drake and would like to know how to reinstall the sda and sdb disks shown below as raid1 without loosing the existing data. They previously ran under Breezy Badger

michael@ubuntu:~$ cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 sda1[0] sdb1[1]
      244195904 blocks [2/2] [UU]

-----------------------------------------------

michael@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1912    15358108+  83  Linux
/dev/hda2            1913       14593   101860132+   f  W95 Ext'd (LBA)
/dev/hda5           11475       14215    22017051   83  Linux
/dev/hda6           14216       14593     3036253+  82  Linux swap / Solaris
/dev/hda7            1913        3824    15358077   83  Linux
/dev/hda8            3825        7489    29439081   83  Linux
/dev/hda9           11161       11474     2522173+  82  Linux swap / Solaris
/dev/hda10  *        7490       11007    28258303+  83  Linux
/dev/hda11          11008       11160     1228941   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/md0: 250.0 GB, 250056605696 bytes
2 heads, 4 sectors/track, 61048976 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table
michael@ubuntu:~$

---

