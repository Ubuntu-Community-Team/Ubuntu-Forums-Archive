---
title: "/def/hdc: No such file or directory"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by Ubuntist on 2005-11-29
Lately when booting up Breezy, I've been seeing the following flash on the screen:
[INDENT]
Setting disc parameters...
/def/hdc: No such file or directory
[/INDENT]
(and yes, it really is /de**f**/hdc, not /dev/hdc).

Most things seem to be working OK, but it makes me a little nervous.  Is there anything I can or should do about this?

---

### Post by myha on 2005-11-29
Can you please paste your fstab:
```
gedit /etc/fstab
```

---

### Post by Ubuntist on 2005-11-29
[QUOTE=myha]Can you please paste your fstab:
[/QUOTE]

Here 'tis:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc     defaults        0       0
/dev/hdc7       /               reiserfs notail          0       1
/dev/hdc9       /home           reiserfs defaults        0       2
/dev/hdc1       /media/windows  ntfs     umask=0222      0       0
/dev/hdc5       /media/linwin   vfat     umask=0000      0       0
/dev/hdc8       none            swap     sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto  0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto  0       0
/dev/fd0        /media/floppy0  auto     rw,user,noauto  0       0

```

---

