---
title: "Help mounting previous linux partition"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by marcusgleason on 2006-12-01
I need to know how to mount a previous Linux partition from a previous install.  It is ext3 file architecture, /dev/sda2.  It's a 100gig (out of a 160gig hdd) partition that has music files and text documents on it.

---

### Post by aysiu on 2006-12-01
```
sudo mkdir /media/recovery
sudo mount -t ext3 /dev/sda2 /media/recovery
gksudo nautilus
```

---

