---
title: "Edgy Eft NTFS Read-Only, No deleting or writing."
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Hyprkookeez on 2007-04-12
I can't write, or delete anything off my ntfs drives through ubuntu edgy eft (64bit), and i have no idea where to start to get this working.
My googling and searching the forums has brought me no success in finding the answer =(.

I'm running 6.10 Edgy Eft (64 bit version).
Here's my fstab information if it helps.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc3
UUID=1ae45bc1-f811-499e-8290-c3a4fb555a40 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc6
UUID=ad34078d-039b-4cd9-9867-3124b8b69ca3 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660  user,noauto         0    0
/dev/hdb        /media/cdrom1   udf,iso9660  user,noauto         0    0
/dev/           /media/floppy0  auto         rw,user,noauto      0    0
/dev/hdc1       /media/windows  ntfs         nls=utf8,umask=0222 0    0
/dev/sda1       /media/300gb    ntfs         nls=utf8,umask=0222 0    0
/dev/sdb1       /media/500gb    ntfs         nls=utf8,umask=0222 0    0

```

---

### Post by Raptor45 on 2007-04-12
You could try:

```
sudo apt-get install ntfs-config
```

And look in Applications>System Tools>NTFS Configuration Tool.

(This may be in Feisty only? Not sure, but give it a try.)

---

### Post by zvacet on 2007-04-12
[http://easylinux.info/wiki/Ubuntu:Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only]("http://easylinux.info/wiki/Ubuntu:Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")

---

### Post by Dual Cortex on 2007-04-12
Do you have the ntfs-3g drivers installed, etc.?
Ubuntu does not natively support writing/deleting anything from NTFS partitions (in other words, any NTFS partitions you have will be read-only). The ntfs-3g drivers allow for writing/etc. but AFAIK they are *still* beta.
Here's an easy how-to:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Can't give you any comments, as I have never tried them.

---

### Post by Hyprkookeez on 2007-04-12
Alright, it works now.
I was wondering why it wasn't working, but all it took was a restart. :( 
anyways, it's all good now. :D 
sorry about that.

---

