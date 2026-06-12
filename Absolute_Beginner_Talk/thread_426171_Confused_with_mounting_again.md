---
title: "Confused with mounting again"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by merike on 2007-04-28
I need to access ntfs partition from live cd. I mount it from terminal and then get this no permissions warning when trying to view contents. It's probably something simple I'm missing, but I can't seem to figure it out.

---

### Post by taurus on 2007-04-28
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
df -h
```
Asusming /dev/hda1 is your Windows partition.

---

