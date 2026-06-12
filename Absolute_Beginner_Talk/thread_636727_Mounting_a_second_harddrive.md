---
title: "Mounting a second harddrive"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by btwong on 2007-12-10
I have looked at [This thread]("http://ubuntuforums.org/archive/index.php/t-386646.html"), but my specs are a bit different:

My sudo fdisk -l looks like this:
> sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        7471    29294527+  83  Linux
/dev/sda3            7472        7957     3903795   82  Linux swap / Solaris
/dev/sda4            7958       19457    92373750    f  W95 Ext'd (LBA)
/dev/sda5            7958       19457    92373718+   7  HPFS/NTFS


my cat /etc/fstab looks like this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=437cfd27-9ba6-4b6a-97f9-65157b5f5e73 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7488D09088D051EA /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=8ef58e02-b889-4244-887a-1db01aa1fb39 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

my question is this: I want to mount my extended ntfs partition (sda5). I have made a folder called /media/Storage Can i just add the below line to my fstab and this will do it?

> /dev/sda5   /media/Storage   ntfs   defaults,umask=007,gid=46 0   1

Or do i need to change some of the settings? (I hatee having to manually mount the drive everytime i log on, especially since all my emails and music are on it.

thanks

---

### Post by kpkeerthi on 2007-12-10
Do you prefer to mount it read-only or read/write?

---

### Post by btwong on 2007-12-10
read and write.

thanks

---

### Post by kpkeerthi on 2007-12-10
```

/dev/sda5 /media/Storage ntfs-3g defaults 0 0

```

Note: I assume you are using gutsy.

---

### Post by btwong on 2007-12-10
cool.

thanks a bunch.

---

