---
title: "Mounting Windows XP"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by DarkPhoenixTSi on 2007-03-05
Okay, I have searched, and followed what I have read to the T, and I still cannot mount my Windows XP drive.

This is my fdisk -l

darkphoenix@KRATER2:~$ sudo fdisk -l
Password:

Disk /dev/hda: 100.0 GB, 100030242816 bytes
16 heads, 63 sectors/track, 193821 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           3       81272    40960000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           81282      189195    54388057+  83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3          189195      193816     2329425    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hda5          189195      193816     2329393+  82  Linux swap / Solaris



I followed the directions [here]("http://ubuntuforums.org/showthread.php?t=375928&highlight=Mounting+Windows+XP"), and I still cannot get to it.

It is driving me NUTS!!!

EDIT:Here is my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb0       /media/hda1     ntfs    umask=0222  0    0


Thanks

---

### Post by aberry5555 on 2007-03-05
it seems like you f-stab isn't written properly, if the bottom line is meant to be for windows xp it should be "/dev/hda1" rather than "/dev/hdb0"

---

### Post by DarkPhoenixTSi on 2007-03-05
Wow!! I can't beleive I didn't catch that!!

Thanks man!

---

