---
title: "trouble mounting cdrom"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by DerekV on 2007-03-27
Alright so i just noticed i cant mount my cdrom.

When i try to mount it I get error /dev/hdb does not exist.

ls /dev/hd* shows only 

```
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda5
```


fdisk -l shows

```
 sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7111    57119076   83  Linux
/dev/hda2            7112        7296     1486012+   5  Extended
/dev/hda5            7112        7296     1485981   82  Linux swap / Solaris
```

fstab file........

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=bfe5bdfd-d451-47df-89ff-054402054aaa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=800bba11-5014-4b8c-954e-cb13fd9333fe none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Any help would be great as im stuck and do not know where to go now....

---

### Post by DerekV on 2007-03-27
bump.

---

### Post by DerekV on 2007-03-27
bump

---

