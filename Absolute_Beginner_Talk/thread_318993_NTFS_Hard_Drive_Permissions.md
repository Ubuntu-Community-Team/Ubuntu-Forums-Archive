---
title: "NTFS Hard Drive Permissions"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by civic_si on 2006-12-14
I am having an issue with mounting my windoze hard drives. I can get them to mount just fine but they are read only. Here is my fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=4ff3959f-46ea-4731-b01c-80dba7320878 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=7563b9fc-09a3-4b13-bdba-14cd3c275568 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdb1	/media/closet	ntfs nls=utf8,umask=0222    0	    0
/dev/hda1	/media/windows	ntfs nls=utf8,umask=0222    0	    0

```

This is exactly like the one on my 6.10 server and that one works just fine. Any suggestions

by the way the OS is 

phoenix@FUSION:/$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"

Thanks

---

### Post by taurus on 2006-12-14
If you want to write to your ntfs, you need to install ntfs-3g...

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by civic_si on 2006-12-14
Thanks Taurus I will try that.

---

