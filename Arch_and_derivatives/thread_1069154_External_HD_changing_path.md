---
title: "External HD changing path"
date: 2009-02-13
forum: Arch and derivatives
---

### Post by gjoellee on 2009-02-13
I have an external HD on 1TB. It has the NTFS system, and I have added it to /etc/fstab and it works great. The annoying thing is that the HD keeps changing path every time i plug it in. One time it is on /dev/sde1, then one other time it is on /dev/sdd1, annd that does so I have to edit /etc/fstab before every time i plug in the HD.

Does anyone know why this happens and/or how to fix it, it is really annoying!?

---

### Post by Barrucadu on 2009-02-13
Do you need it to be in fstab? Why not just use HAL and automatic mounting?

---

### Post by Toffeeapple on 2009-02-14
Would identifying the drive by it's "Universally Unique IDentifier" in fstab maybe help?

to find it while it's plugged in..
$ /bin/ls -lF /dev/disk/by-uuid/

and then a line something like this in your fstab..

UUID=C81032F51032EA58 /mnt/WinXP ntfs-3g users,uid=1000,gid=100,fmask=0113,dmask=0002 0 0

read about it [here]("http://wiki.archlinux.org/index.php/Persistent_block_device_naming")

---

### Post by Nepherte on 2009-02-14
As said before, use UUIDs. They were introduced precisely for this issue. UUIDs don't change. To determine the UUIDs you can use the command blkid:
```
blkid
```

---

### Post by gjoellee on 2009-02-14
I just moved over to GNOME, and somehow the external HD automounts as well! In KDE I had to do all that form the terminal!

---

