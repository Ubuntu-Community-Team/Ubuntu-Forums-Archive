---
title: "How do I access tunes from my CD?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by the beak on 2008-03-05
All I'm trying to do is access tunes on my CD to my laptop.

O'm using Damn small linux and have etc/fstab of 
/dev/hda2  /  ext3  defaults,errors=remount-ro  0  1
proc  /proc  proc  defaults  0  0
/dev/fd0  /mnt/auto/floppy  vfat  defaults,owner,noauto,showexec  0  0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
# Added by KNOPPIX
/dev/hda1 none swap defaults 0 0


Can anyone explain a way to access the CD. I undertsand that it has to be mounted but nothing I do works.

Please help.

---

### Post by oldos2er on 2008-03-05
Damn Small Linux forums are here: [http://www.damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi](http://www.damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi)

---

### Post by the beak on 2008-03-05
I thought being debian it would be similar?

---

### Post by spiderbatdad on 2008-03-05
you might try changing to look like this:```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
``` I'm assuming you had UUID= information before the entry, and you left it out.

---

