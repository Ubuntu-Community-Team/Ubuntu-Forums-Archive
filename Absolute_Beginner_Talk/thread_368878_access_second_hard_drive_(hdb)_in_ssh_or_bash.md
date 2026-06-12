---
title: "access second hard drive (hdb) in ssh or bash"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by uberdrah on 2007-02-23
Hi,

I've finally managed to get kubuntu installed and i am loving the ease at which openssh install - apt-get install openssh - brilliant.

Ok some back ground into what i have done after post kubuntu installation.  I added a second hard drive i found lying around, formatted it and mounted it in the /media directory so my fstab file now looks like this:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1        /media/stuff    ext3    defaults        0       0

The problem i am having is that i don't know how to access hdb1 when i ssh from m laptop to the Linux machine.

if i cd /media and then ls -l i get the output below, stuff is highlight (as if the I'd used the mouse to highlight it) and i am unable cd /stuff?

lrwxrwxrwx 1 root root    6 2007-02-21 23:20 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-02-21 23:20 cdrom0
lrwxrwxrwx 1 root root    7 2007-02-21 23:20 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2007-02-21 23:20 floppy0
drwxrwxrwx 4 root root 4096 2007-02-24 01:27 stuff

I've probably missed some very basic and any help would greatly appreciated.

Thanks

Rich

---

### Post by taurus on 2007-02-23
Actually, that would be either

```
cd /media
cd stuff
-or-
cd /media/stuff
```

---

### Post by uberdrah on 2007-02-23
Thanks taurus, it must the fact thats it 2 in the morning that i didn't think of that.

---

