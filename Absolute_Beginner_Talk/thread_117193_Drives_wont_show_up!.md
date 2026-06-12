---
title: "Drives wont show up!"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2006-01-14
I'm using KDE. When I click storage media my drives no longer show up, except the floppy. They all showed up before I editted my /etc/fstab and rebooted. Here is my fstab;

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1 /media/hda1 ntfs umask=0222 0 0
/dev/hdd5 /media/hdd5 ntfs umask=0222 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Thanks!

---

### Post by aysiu on 2006-01-14
Your /etc/fstab looks fine to me. It's probably an ivman issue, though. Do you have ivman installed?

---

