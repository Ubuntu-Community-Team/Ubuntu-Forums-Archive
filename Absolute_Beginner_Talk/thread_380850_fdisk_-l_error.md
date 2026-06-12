---
title: "fdisk -l error"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by pilot550 on 2007-03-10
When I type sudo fdisk -l I get:

steve@tsunami:~$ sudo fdisk -l
Password:

Unable to seek on /dev/sda
steve@tsunami:~$

Is that normal? How can I fix this.

---

### Post by teaker1s on 2007-03-10
this is not normal, searching forums / google several things come up regarding hard drive partitions-have you looked  to see if you can find an accurate answer?

---

### Post by pilot550 on 2007-03-10
I've searched everywhere. I can't find an answer. The only thing I can figure is that it can't read my SATA drives because they are in raid. If I take out the sudo and just do fdisk -l I get:
steve@tsunami:~$ fdisk -l

Disk /dev/sdc: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7872     2015216    e  W95 FAT16 (LBA)
steve@tsunami:~$
which is the partition I set up on an IDE drive and mounted as /media/share.

---

### Post by teaker1s on 2007-03-10
so could it in fact be a sudoers issue rather than  fdisk -l / hardrive
mine
> daniel@ubuntu:~$ fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19269   154778211   83  Linux
/dev/hda2           19270       19457     1510110    5  Extended
/dev/hda5           19270       19457     1510078+  82  Linux swap / Solaris
daniel@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19269   154778211   83  Linux
/dev/hda2           19270       19457     1510110    5  Extended
/dev/hda5           19270       19457     1510078+  82  Linux swap / Solaris
daniel@ubuntu:~$




---

