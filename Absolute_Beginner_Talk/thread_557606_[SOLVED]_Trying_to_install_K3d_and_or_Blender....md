---
title: "[SOLVED] Trying to install K3d and or Blender..."
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-09-22
I am trying to install blender from the terminal and then i get this```
Media change: please insert the disc labeled
 'Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in the drive '/cdrom/' and press enter

```
since 7.04 was an update for me I do not have this cd.  i have the 7.04 live cd.  What do I do in this case?? :confused:

Edit: also get the same for K3D

---

### Post by yabbadabbadont on 2007-09-22
Edit your /etc/apt/sources.list file and comment out the line(s) that refer to the CD.  Then run "sudo apt-get update".  It shouldn't prompt you for the CD after that.

---

### Post by Linux_Man on 2007-09-22
Try installing from apt-get


```
sudo apt-get install k3d

sudo apt-get install blender
```


On the terminal.

---

### Post by mramsey on 2007-09-22
That did the trick. Thanks!

---

