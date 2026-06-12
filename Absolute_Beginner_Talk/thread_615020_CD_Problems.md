---
title: "CD Problems"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by ytowngeek on 2007-11-16
I'm using ubuntu 7.10 on an older Gateway ProM 866.  If I have a data cd in the drive when I first boot, i can read it.  but then I can't change cd's.  Audio CD's don't work whether they're in at startup or not.  I have an IDE CD-ROM, but it shows as sdb


Here's my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dbe68924-2a6b-4d11-96ad-630fe3c0620e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4251a1cd-f377-4b5e-b455-0dcbf019dc82 none            swap    sw              0       0
/dev/sdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Any help would be appreciated.

---

### Post by Inxsible on 2007-11-16
Try commenting out the entry for the cdrom, save the file and then try again. CDRoms are like external drives and they should get mounted automatically. you don't need it in the fstab

---

