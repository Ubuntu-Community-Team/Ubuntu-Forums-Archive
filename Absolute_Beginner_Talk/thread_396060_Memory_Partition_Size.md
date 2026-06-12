---
title: "Memory Partition Size???"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by wodz9798 on 2007-03-29
I recently installed Xubuntu 6.10 and used the installer's default settings for the partitioning. I have a 20GB hd. I tried to install some new programs and it says I have run out of disk space. Clearly i have got enough disk space so what is going on? I have provided some info below that may be useful.   


wodz@IBMPentium3:~$ sudo fdisk -l
Password:

Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2377    19093221   83  Linux
/dev/hda2            2378        2482      843412+   5  Extended
/dev/hda5            2378        2482      843381   82  Linux swap / Solaris

wodz@IBMPentium3:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           630        401        229          0         70        195
-/+ buffers/cache:        135        495
Swap:          823          0        823

wodz@IBMPentium3:~/Desktop$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              18G  1.6G   16G  10% /
varrun                316M   76K  316M   1% /var/run
varlock               316M     0  316M   0% /var/lock
procbususb             10M   84K   10M   1% /proc/bus/usb
udev                   10M   84K   10M   1% /dev
devshm                316M     0  316M   0% /dev/shm
lrm                   316M   18M  299M   6% /lib/modules/2.6.17-10-generic/volatile

---

### Post by Patrick K on 2007-03-29
I don't think the file tools provided are at all accurate. Take a look at this post: [http://www.ubuntuforums.org/showthread.php?t=372324](http://www.ubuntuforums.org/showthread.php?t=372324)
Several partitions are incorrectly sized. If you have another way to check the size, like a win boot disk or other bootable utilities, I'd see what they say.

---

