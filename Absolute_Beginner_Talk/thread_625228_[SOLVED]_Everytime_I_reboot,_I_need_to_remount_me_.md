---
title: "[SOLVED] Everytime I reboot, I need to remount me HDD's from partitioneditor.  what g"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Tdukes on 2007-11-27
I really dont get it.  Heres my fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c40d0039-50e2-4b09-8d2a-32a986c8c4b5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=aaa3a388-ee9f-460e-b55e-6f4ffb41b9a1 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

/dev/sdb5 /media/Media ext3 default 0 0
/dev/sdc5 /media/Storage ext3 default 0 0

I guess default should be "defaults" huh

---

### Post by Inxsible on 2007-11-27
For hdb and hdc, you have noauto = do not automount. Change that to auto and you should be good to go :)

And yes, it should be defaults, with the s, for the EXT3 partitions that you have.

---

