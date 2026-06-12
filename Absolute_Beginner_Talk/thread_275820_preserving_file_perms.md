---
title: "preserving file perms"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by rpm13 on 2006-10-11
If I start audacity as an ordinary user it complains about io error
Started as root its ok
And it becomes ok if permission of /dev/dsp is changed to rw for all (by default its rw only for root)

The problem is that Ive to do this every time I boot the machine.

So how does one preserve permissions of device files across boots?

---

### Post by CatKiller on 2006-10-12
How were you changing the permissions of /dev/dsp? Permissions are normally retained after a reboot.

The easiest, and potentially most dangerous, way is to run ```
gksudo nautilus
``` right-click on /dev/dsp and select Permissions. Mine, that I haven't fiddled with, has file owner as root, file group as audio, and read/write permissions for owner and group, and everything works fine. Are you a member of the audio group?

---

