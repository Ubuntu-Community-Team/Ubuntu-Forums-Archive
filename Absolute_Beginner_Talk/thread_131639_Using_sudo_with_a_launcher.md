---
title: "Using sudo with a launcher"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2006-02-16
I can't figure it.  For instance, I've got a gdesklet widget that shows me the free space on each of my drives.  Presently, I associate them with the command **nautilus /media/fatdrive** and suchlike.  What I really want to do is open that as root, but I can't get it to recognize the sudo command. :confused:

---

### Post by xtacocorex on 2006-02-16
Try gksudo. I know there are more than one for Gnome, but since I run KDE, I can't be totally sure. 

Hope this helps some.

---

### Post by aysiu on 2006-02-16
```
gksudo nautilus /media/fatdrive
```

---

