---
title: "Dual boot, disc full after mounting shared partition"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Conq321 on 2008-01-09
Hi,

i've been looking around on this forum and it has helped me with a bunch of things, but there does not seem to be an answer for this particular problem.

I dual boot my laptop (xp ubuntu). I have a partition (named "dual") that contains my work documents, and than of course the other partitions for the os's.

This partition (dual) is mounted at startup in Ubuntu. Problem is, it gets quite full and now Ubuntu is giving me messages that my disc is full and refuses to download, save or do anything else on that partition that requires disc space.

The ext3 partition on which ubuntu is installed, is 5gb large. Running "disc usage" learns me that the "dual" partition is seen as a content of this filesystem after mounting (as /media/hda6, uses 90% of the filesystem's capacity (5gb)).

Does this mean I must resize my ext3 partition? That would implicate that I can only use half of my resources!!! (Ext3 must be as big as "dual" to mount it?!) Or are there any solutions?!

Don't know if it helps, but here's my fstab: (hda1 and hda2 are not mounted, i modified this myself. hda1 is my recovery and hda2 is the partition on which windows is installed)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=a8d8f990-19f1-43ce-9447-4e1c11c61c5f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
 UUID=70BC-0FC7  /media/hda1     vfat    noauto,ro,nouser,noexec,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=309C26B19C267210 /media/hda2     ntfs    noauto,ro,nouser,noexec,umask=007,gid=46 0       1
# /dev/hda6
UUID=7E572471119F0284 /media/hda6     ntfs    defaults,umask=1000,gid=1000 0       1
# /dev/hda5
UUID=31997993-fd05-4650-9fc6-5545c291ec7f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by dcstar on 2008-01-09
> **Conq321 said:**
> Hi,

i've been looking around on this forum and it has helped me with a bunch of things, but there does not seem to be an answer for this particular problem.

I dual boot my laptop (xp ubuntu). I have a partition (named "dual") that contains my work documents, and than of course the other partitions for the os's.

This partition (dual) is mounted at startup in Ubuntu. Problem is, it gets quite full and now Ubuntu is giving me messages that my disc is full and refuses to download, save or do anything else on that partition that requires disc space.
........

```
df -h
```will show you the usage on all mounted partitions.

---

### Post by Conq321 on 2008-01-11
Ok , thanks a lot. It learns me that my linux partition is full as well :) I'll make it bigger.

---

