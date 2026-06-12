---
title: "Using Gparted"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-10-31
I was wondering how to use Gparted within ubuntu I downloaded it through the synoptic manager, but I can't find it anywhere

---

### Post by ofb on 2007-10-31
Alt-F2, then enter

gksudo gparted

---

### Post by Cochise on 2007-10-31
Click System in the menu bar at the top of the screen then adminstration its in there called partiton editor

---

### Post by Mothinator on 2007-10-31
It should be under System->Administration->Partition editor

If not press ALT+F2 and type "gksu gparted"

---

### Post by -grubby on 2007-10-31
it should be in the menus somewhere called "gparted" or "partition editor" otherwise open a terminal (alt+F2) and type gksudo gparted

---

### Post by dhughes on 2007-10-31
I thought it added it under System>Administration but I just installed it too and it isn't there.

 You could use "locate" to see where it is and make a link to it. I'm not sure if that's the proper way to do it or not.

 FYI if you do use it you can't use it on a mounted partition, when I use it I use it on a  bootable CD by itself, the Ubuntu LiveCD/Install CD should have it on there under Administration I believe. That way no disks are mounted when you use it.

---

### Post by Drakkor on 2007-10-31
Just so you know, it's probably better to just download the live GParted CD,because most heavy work must be done with your hard disk(s)
unmounted and not being used. You boot to the CD and then you can work on your actual hard drives.

---

### Post by Cochise on 2007-10-31
gparted live cd is great, well worth the download and disc

---

