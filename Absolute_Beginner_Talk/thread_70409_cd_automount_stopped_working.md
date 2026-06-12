---
title: "cd automount stopped working"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by specialsource on 2005-09-29
Hi all.. 
when i insert a cd/dvd, ubuntu usually automounts it, and put a shortcut on the desktop so i can browse it.
but this has suddenly stopped working. i have to mount the cd manually everytime i insert a cd.
I've checked Removable Drives Preferences and i've ticked all mount media options. but still doesnt have any effect.
can anyone help please..
Thanks!

---

### Post by mlomker on 2005-09-29
What does your /etc/fstab file look like?  An incorrect entry for your CD-ROM drive can do that.  

Do you get any errors on boot-up regarding the gnome-media-manager or HAL?

---

### Post by specialsource on 2005-09-29
Thanks for the quick reply!.. 
There was no error msgs on boot up
here's my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/windows	vfat	iocharset=utf8,umask=000	0	0

```
[QUOTE=mlomker]What does your /etc/fstab file look like?  An incorrect entry for your CD-ROM drive can do that.  
Do you get any errors on boot-up regarding the gnome-media-manager or HAL?[/QUOTE]

---

### Post by mlomker on 2005-09-29
I don't see a problem with the fstab.  I found [this thread]("http://www.ubuntuforums.org/showpost.php?p=31490&postcount=7") that has a command for verifying that hal is running.

Hopefully someone else will jump in with some ideas.

---

### Post by specialsource on 2005-09-29
i've fixed this by modifying permission for HAL
in desktop menu:
- System - Admin - User/Groups
- find user: HAL
- add privilages to CD ROM
RESTART dbus 
in terminal:
sudo /etc/init.d/dbus-1 restart
-DONE-

---

