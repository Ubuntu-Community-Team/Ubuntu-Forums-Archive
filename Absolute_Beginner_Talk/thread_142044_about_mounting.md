---
title: "about mounting"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by mlind on 2006-03-09
can I somehow mount existing directory, say ~/tmp/game2
using loopback interface as /media/cdrom ?

---

### Post by JShadow on 2006-03-09
you could use a link, although you'd have to remove the /media/cdrom directory

ln -s ~/tmp/game2 /media/cdrom

What are you trying to achieve exactly?

---

### Post by mlind on 2006-03-10
[QUOTE=JShadow]you could use a link, although you'd have to remove the /media/cdrom directory

ln -s ~/tmp/game2 /media/cdrom

What are you trying to achieve exactly?[/QUOTE]

well, I'm trying to mount certain directory for cedega to use.
I've done this before by making .iso image out of directory contents and mounting
image on loopback device.

---

