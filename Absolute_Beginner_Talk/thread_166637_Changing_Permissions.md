---
title: "Changing Permissions"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-04-26
Hi i'm new to ubuntu and my old windows hard drive which is ntfs keeps getting auto mounted when ubuntu starts up and i'm wondering how to change the permission on it so that i can read the files. Here's a picture of the mounted harddrive.

[IMG]http://img133.imageshack.us/img133/5408/screenshot2ku.png[/IMG]

Thanks for the help

---

### Post by manicka on 2006-04-26
can you post the content of your /etc/fstab file

---

### Post by cptjaben on 2006-04-26
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdb1       /media/hdb1     vfat    iocharset=utf8,umask=000   0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by ob211 on 2006-04-26
change this line
```
 /dev/hda1 /media/hda1 ntfs defaults 0 0 
```
to this
```
 /dev/hda1 /media/hda1 ntfs defaults,user 0 0 
```

---

### Post by manicka on 2006-04-26
Something like this used to work for me. Luckily I have no need to access any ntfs partitions at the moment.

```
/dev/hda1 /media/hda1 ntfs	defaults,umask=002,nls=utf8	0	0
```

---

### Post by Mustard on 2006-04-26
This guide says to use this...

```
/dev/hda1    /media/hda1 ntfs  nls=utf8,umask=0222 0    0
```

[http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

