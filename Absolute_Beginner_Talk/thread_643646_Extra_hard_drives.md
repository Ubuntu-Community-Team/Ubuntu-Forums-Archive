---
title: "Extra hard drives"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by essendon on 2007-12-18
Hello all

I have two extra internal hard drives.  One is a sata and one is ide.  They mount at start up as I have added them in the fstab, but they are both read only.

here is the fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ae1e3c7a-eb10-4cb0-95f4-0d3363a386f9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=7071e76e-6f21-4f0f-b15b-78505103878d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdb1	/home/kelianh/par1 vfat defaults 0 0
/dev/sda1	/home/kelianh/par2 vfat defaults 0 0


how should the last two entries read?

---

### Post by kpkeerthi on 2007-12-18
You need to set appropriate umask for VFAT.

For example:
```

/dev/hdb1 /home/kelianh/par1 iocharset=utf8,umask=000  0    0

```

---

