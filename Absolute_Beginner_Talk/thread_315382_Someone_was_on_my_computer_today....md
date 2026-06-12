---
title: "Someone was on my computer today..."
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2006-12-09
Someone was on my computer while I was at work, and they changed some crazy setting.

[IMG]http://i3.photobucket.com/albums/y88/cheaptrick905/omgno.png[/IMG]

Those weren't there before... I think (not for sure) the floppy one was there but I don't recall having all those CD ones being there.

I have no idea what to change because the person who did this is five and all they had to say was "Idunno" about the whole thing, not even realizing what they did.

Well... I do like it when my Sansa player is plugged in and that directory shows up, but I don't even have that many CD drives and they are all being shown. Can someone help?

---

### Post by beefcurry on 2006-12-09
woah~ not alot of people with sansa players :D i have one too !

To get to the point, i see your have an ISO in that directory, could it be you have a mount script?? I would think that someone mounted the iso many many times. hence there being soo many CD-Drives. If they appear on your Desktop use an unmount script to amount them or somthing similar. (i.e. try ejecting them, or just manually unmounting them)

---

### Post by SZF2001 on 2006-12-09
There are no mounted icons in the desktop... How do I do it manualy, or through to terminal?

---

### Post by konst88 on 2006-12-09
Post the output:
```
cat /etc/fstab
```

---

### Post by SZF2001 on 2006-12-09
Here's what I got:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom2   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom3   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom4   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom5   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom6   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom7   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom8   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

So it IS saying something about "iso"... But now what do I do?

---

### Post by konst88 on 2006-12-09
So delete all the duplicated lines from this file, and leave only one if you need this iso mounted:
```
sudo gedit /etc/fstab
```

---

### Post by SZF2001 on 2006-12-09
Looks like that did the trick! Thanks guys.

---

