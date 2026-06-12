---
title: "GParted"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by buddingh4x0r on 2007-12-03
I installed gutsy and everything's working fine, except for one thing that's really been bugging me... namely, my partitions. When gutsy installed, I did the guided partitioner, and set it to give gutsy 100gb and windows 60bg. Unfortunately, it apparently got them the wrong way around, and now I want to resize them back >.<
I downloaded GParted, but it won't let me modify my partitions... resize/move is greyed out, as is unmount. any ideas?

---

### Post by wormser on 2007-12-03
Gparted cannot modify mounted drives.  Since you are logged into Ubuntu the drive is mounted.  I would recommend backing up all your data.  Then boot into the live CD and run Gparted.

---

### Post by jromer on 2007-12-03
burn a copy of the gparted live iso to a CD.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Partitions need to be unmounted in order to adjust them. Booting from the Live GParted CD is the easiest thing I've found.

EDITED ** After reading the prior post (I didn't see it before I posted) I hadn't realized that GParted was now on the live CD. I was used to the Dapper Drake Live CD which didn't have GParted as a default. (You had to open some additional repositories and then install GParted via Synaptic.) But  the Live GParted CD is an option.

---

