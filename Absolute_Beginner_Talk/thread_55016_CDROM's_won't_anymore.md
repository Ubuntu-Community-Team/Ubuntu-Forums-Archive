---
title: "CDROM's won't anymore"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-08-07
I've posted this before, but it seems the thread never was posted.

My CDROM's won't mount anymore. I gothe following form cat fstab:

> jacques@HomePC:~ $ cat /etc/fstab # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdh1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdh5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hde1       /media/win_master       ntfs    nls=utf8,umask=0222 0 0
/dev/hdf1       /media/win_slave        ntfs    nls=utf8,umask=0222 0 0

And this from cat mtab:

> jacques@HomePC:~ $ cat /etc/mtab /dev/hdh1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev/hde1 /media/win_master ntfs rw,nls=utf8,umask=0222 0 0
/dev/hdf1 /media/win_slave ntfs rw,nls=utf8,umask=0222 0 0
usbfs /proc/bus/usb usbfs rw 0 0



And this from ls -lah /dev/cd*

> jacques@HomePC:~ $ ls -lah /dev/cd*
ls: /dev/cd*: No such file or directory

Fro the life of me, I cannot get my cdrom's to work anymore.
Any ideas?

---

