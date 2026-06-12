---
title: "CDROM and kernel buggered"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-08-04
I have tried to update the kernel to 2.6.10 and a folder has appeared under /usr/src showing kernel-headers 2.6.10-5 386 but upon boot I still get 2.6.8-1 386. Why won't this change or am I understanding the process wrong. After synaptic closed and a restart, my video was buggered as well as my cdrom's won't mount. ](*,) 

Here is the ouput from cat fstab, mstab and my devices file. When trying to access my CDROM's i get this response. "mount: special device /dev/hdb does not exist"

The help files and a search on this forum was/is unable to solve my issue.
Hope for help!!! \\:D/ 

> jacques@HomePC:~ $ cat /etc/fstab
# /etc/fstab: static file system information.
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

jacques@HomePC:~ $ cat /etc/mtab
/dev/hdh1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev/hde1 /media/win_master ntfs rw,nls=utf8,umask=0222 0 0
/dev/hdf1 /media/win_slave ntfs rw,nls=utf8,umask=0222 0 0
usbfs /proc/bus/usb usbfs rw 0 0

jacques@HomePC:~ $ ls -lah /dev/cd*
ls: /dev/cd*: No such file or directory

---

