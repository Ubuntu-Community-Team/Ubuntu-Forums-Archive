---
title: "Partitioning ruins my XP install."
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by GuitarRocker2562 on 2007-03-31
Everytime I mess with my XP partition my system goes bye bye. I am using ubuntu more now and wish to make the partition larger. However, I do not want to mess up my XP install, how do I do this?

---

### Post by annda on 2007-03-31
the safest way i know (and tried) is:

1) defragment your windows partition under win.
2) boot from gparted live cd [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) and resize the partitions to your liking.

after rebooting to xp you will get a bunch of errors (because it's partition info has changed) but let the disk check correct them and you should be fine.

---

