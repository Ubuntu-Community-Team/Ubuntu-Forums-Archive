---
title: "DVD Drive Recognition"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Don_Juan on 2007-06-07
So I just recently installed Ubuntu for the first time last night.  It has a lot of stuff I like so far.  I got one DVD (data) to be recognized, and I could take stuff from, but now the DVD's don't show up, and it says it can't mount or eject because there's probably no media.  I know the DVD works though.....Is there a Kernel / Driver I can find... or how can I fix this so that it's working properly?  Under properties it appears to be looking at the correct one... so I'm very confused!  Also am I by default supposed to have a drive of some sort (Hard Drive for instances on Mac, or My Computer on PC) on the desktop?  Thanks much!

---

### Post by Inxsible on 2007-06-07
[SIZE=2]Can you post the output of the following commands:[/SIZE]
 
```
uname -r
gedit /etc/fstab

```

---

### Post by eddieb on 2007-06-07
Place the disc in the drive and do a complete reboot.

---

### Post by warcriminal on 2007-06-07
Read this article;

[http://www.goitexpert.com/entry.cfm?entry=Play-DVDs-on-UBUNTU](http://www.goitexpert.com/entry.cfm?entry=Play-DVDs-on-UBUNTU)

---

### Post by Don_Juan on 2007-06-07
> **Inxsible said:**
> [SIZE=2]Can you post the output of the following commands:[/SIZE]
 
```
uname -r
gedit /etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6b0b65e2-f3e5-4f45-bb33-5bd30b3f3e2d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fae225bd-9c3b-4b39-bcc1-d9463cdd6ba8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

When I got home today, and rebooted my computer it did have the DVD in it.  I just don't understand that inconsistency.  Thanks to everyone who has answered, already!

---

### Post by Don_Juan on 2007-06-07
Alright. It seems to be that the first DVD I put in, always works, it's after I eject it, and then put a new one in without restarting, that it doesn't work.

---

