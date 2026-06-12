---
title: "Resizing linux partition...."
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by adt41287 on 2007-05-01
i want to make my ubuntu partition bigger... is there any way to do this? easily ha:confused:

---

### Post by phiphedog on 2007-05-01
you can use gparted

[COLOR="Red"]sudo apt-get install gparted[/COLOR]

then just type 

[COLOR="Red"]sudo gparted[/COLOR]

to get it running. It's all graphical so it should be self explanitory once you have it loaded.

---

### Post by Billy McCann on 2007-05-01
You'll need a GParted LiveCD or you can use your Ubuntu LiveCD.  (You cannot unmount your Ubuntu partition from within your hdd booted system, you have to use a LiveCD).  

You can get the GParted LiveCD here;
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Download it, burn it, boot into it.  It's graphical, so just expand the Ubuntu partition to the right.  Careful resizing any Windows partitions.

---

