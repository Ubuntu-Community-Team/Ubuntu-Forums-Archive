---
title: "Cannot Mount NTFS Partition in Dolphin under Kubuntu"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by ddrplayer512 on 2008-03-25
I have just installed Kubuntu Gutsy on my nice trusty laptop yesterday. In Ubuntu (I had Ubuntu Gutsy before) I was perfectly able to mount NTFS partitions. But, I can't seem to mount them in the Dolphin File Manager under Kubuntu! I wouldn't mind, but I use Windows XP regularly and I need to access data on that partition while using Kubuntu. Did anyone else have this problem?

---

### Post by glennric on 2008-03-25
Both Kubuntu and Ubuntu use the same method to mount NTFS drives.  That is with either ntfs-fuse or ntfs-3g.  Post the output of 
```
cat /etc/fstab
```
and
```
sudo fdisk -l
```
and we can figure out if it is mounted and how to get it to mount.

---

### Post by ddrplayer512 on 2008-03-26
Sorry for the delay. Here's the output of these two commands:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=409b4da1-1e81-44d8-a491-6b4c31bc2867 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=464b06cf-03f0-4874-9417-51ab5768ea20 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

And...

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d3c4d3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5958    47857603+   7  HPFS/NTFS
/dev/sda2           10819       12030     9735390    c  W95 FAT32 (LBA)
/dev/sda3           12031       12161     1052257+  d7  Unknown
/dev/sda4            5959       10818    39037950    5  Extended
/dev/sda5   *        5959       10613    37391256   83  Linux
/dev/sda6           10614       10818     1646631   82  Linux swap / Solaris

Partition table entries are not in disk order

```

Hope that helps!

---

