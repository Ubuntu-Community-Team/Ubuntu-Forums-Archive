---
title: "Mounted Same HD Twice"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by magnoliablossom on 2006-08-05
I wanted my second hard drive to mount on start up.  All my media files are on it and I wanted to be able to listen to my music while in Ubuntu.  I followed the tutorial here:  [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite") and now it's showing up twice on my desktop and under Places twice.  Here's a copy of the file it told me to edit.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
dev/hdb1    /media/windows vfat  iocharset=utf8,umask=000  0    0

---

### Post by vruum on 2006-08-05
not really sure what's going on, but could you open up a terminal and post the output of the two commands:
```
mount
```

and 
```

cat /etc/mtab
```
?

---

