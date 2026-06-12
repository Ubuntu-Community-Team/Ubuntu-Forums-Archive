---
title: "Mounting XP Fat32 drive in fstab? [Resolved]"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by NewRubberSoul on 2007-01-13
Hello Everyone,

I'm dual booting Edgy and Xp, and each system has it's own hard drive (Linux master, Xp slave).  I've got GRUB set up perfect and everything, but I want to be able to see the XP slave drive when I'm using Ubuntu.

I've got XP formatted as Fat32, so linux should have no problem reading and writing and i think I'm just looking for a quick answer about how to mount the slave drive and have it show up in my media folder. 

Here's the readout of my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=011cb57e-b03f-4993-a203-c78ac29d8f3f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=9da51711-4299-401c-8458-d0d1e4c5ba15 none            swap    sw              0       0
# /dev/hdb1
/deb/hdb1	/media/hdb1	vfat	defaults, errors=remount-ro	0	0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

``` 

I know it's kind of messy, but I'm pretty much a noob when it comes to these things.  You're all the best.  Thank you!

](*,)

---

### Post by aysiu on 2007-01-13
Change this line ```
/deb/hdb1	/media/hdb1	vfat	defaults, errors=remount-ro	0	0
``` to this ```
/deb/hdb1	/media/hdb1	vfat	iocharset=utf8,umask=000	0	0
``` Then reboot.

---

### Post by logos34 on 2007-01-13
there's a typo in the original line: 

it should be 
> /de**v**/hdb1 ....

---

### Post by tonyr1988 on 2007-01-13
You can also choose *where* you want to mount it (at least for me, always going to /media/hdb1 can be inconvenient). If you want it mounted, for example, at /winxp then do this:

> sudo mkdir /winxp

And make your fstab entry this:

> /dev/hdb1	/winxp	vfat	iocharset=utf8,umask=000	0	0

Of course, credit to aysiu :D - I would've forgotten about iocharset.

---

### Post by NewRubberSoul on 2007-01-13
AWESOME!

You all are the best.  I've got it working exactly how I wanted.  Kudos all around!

:mrgreen:

---

