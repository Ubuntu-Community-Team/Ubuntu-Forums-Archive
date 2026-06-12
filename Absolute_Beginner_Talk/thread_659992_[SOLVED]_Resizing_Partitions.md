---
title: "[SOLVED] Resizing Partitions"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-01-06
When i installed Ubuntu 7.10 off the liveCD I did not understand the partitioning part correctly and have made the Ubuntu partition about 15gb smaller than i wanted it to be, just now Windows XP has the larger partition but I want Ubuntu to have the larger partition. Is there any way of resizing the partitions?

---

### Post by taurus on 2008-01-06
You can do that with gparted from the LiveCD or GParted LiveCD again if you wish.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Basically, you want to reduce the size of your windows and merge that free space with Ubuntu partition.  As _always_, back up you important files first before you play around with partition table.

---

### Post by forestpixie on 2008-01-06
try doing it from the ubuntu livecd - it has a partioner - gparted

you could resize the xp partition and then when it's completed resize the ubuntu to take up the slack

Edit - as the man said :) or woman!

---

### Post by jan quark on 2008-01-06
i think you need the Gparted live cd.

have a look here
[HTML]http://gparted-livecd.tuxfamily.org/[/HTML]


ohh sorry for the triple post but when I entered this thread there was none... :)

---

### Post by Fraser from Scotland on 2008-01-06
thats great! thanks alot, but I am totally new to Ubuntu and Linux, so is there a guide anywhere that could,well, guide me on how to do this?
And where is gparted on the live CD?

---

### Post by taurus on 2008-01-06
> **Fraser from Scotland said:**
> thats great! thanks alot, but I am totally new to Ubuntu and Linux, so is there a guide anywhere that could,well, guide me on how to do this?
And where is gparted on the live CD?

Here are some pictures, [http://gparted-livecd.tuxfamily.org/screenshots.php](http://gparted-livecd.tuxfamily.org/screenshots.php).

Gparted should be in System -> Administration of the Ubuntu LiveCD.

---

### Post by Alx c on 2008-01-06
If i were you i would defragment the disk before doing a partition. It makes more space and makes you computer go faster

---

### Post by Fraser from Scotland on 2008-01-06
thanks alot, I'm on the Live CD the now and I defragged my disc before installing Gutsy so I'm guessing it will be ok.

---

