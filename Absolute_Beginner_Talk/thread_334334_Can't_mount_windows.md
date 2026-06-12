---
title: "Can't mount windows"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by ajmorris on 2007-01-08
Why can't i mount windows.


I used to be able to mount my vista partition in feisty fawn but now that i re-installed vista i can't.

I get this error: [PHP]sudo mount hda1
mount: special device /dev/disk/by-uuid/42E48EAFE48EA52F does not exist[/PHP]

this is my /etc/fstab entry too:

[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=1cfc1c89-3f75-4887-a473-c75a6b8da416 /               reiserfs notail          0       1
# /dev/hda1
UUID=42E48EAFE48EA52F /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=8000-9CF6  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=8cbbab28-d426-44e9-af29-953fa53272f8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0[/PHP]

---

### Post by taurus on 2007-01-08
Because it would have a new UUID now.  I would change the UUID to just an old fashion /dev/hda1 in /etc/fstab.

---

### Post by ajmorris on 2007-01-08
sorry i am a noob at fstab.

You mean just get rid of the UUID entry all together?

---

### Post by ajmorris on 2007-01-08
ok i did some fiddling with fstab and got it down to say that /dev/hda1 does not exist.

So i looked in /dev/ and sure enough i don't have any hda block devices. Is this something new in fesity? is that why there was a UUID entry in fstab?

---

