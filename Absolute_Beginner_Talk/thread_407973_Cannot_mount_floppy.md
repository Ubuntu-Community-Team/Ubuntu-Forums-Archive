---
title: "Cannot mount floppy"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by alfonsos on 2007-04-12
I can't seem to remount the floppy after I unmounted it.

Here's the content of /etc/fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto rw,user,noauto     0       0

Here's the printout following the mount command:

alfonso@alfonso-Desktop:~$ mount /media/floppy0
mount: I could not determine the filesystem type, and none was specified

Isn't "auto" a legitimate value for <type>?

Al

---

### Post by zvacet on 2007-04-13
```
sudo mount /dev/fd0 /floppy -t vfat
```

---

### Post by alfonsos on 2007-04-13
$ sudo mount /dev/fd0 /floppy -t vfat
Password:
mount: mount point /floppy does not exist


$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto rw,user,noauto     0       0

---

