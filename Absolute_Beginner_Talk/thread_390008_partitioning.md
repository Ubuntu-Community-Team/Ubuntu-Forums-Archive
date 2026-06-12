---
title: "partitioning"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-03-21
Is there a decent graphical disk partitioner like the one used in the ubuntu installer?

Otherwise, how do i enable unpartitioned space on a usb hdd

---

### Post by dstew on 2007-03-21
You can make a gparted live CD, runs all by itself.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by taurus on 2007-03-21
You mean something like gparted!

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install gparted
```
System -> Administration.

---

### Post by buuntuu! on 2007-03-21
you can also install gparted from the repositories

---

### Post by dgrafix on 2007-03-21
Great !


Thanks much-ly


PS: Is aptitude the new apt-get or something?

---

### Post by taurus on 2007-03-21
Here you go.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by euler_fan on 2007-03-21
As a note, it is usually best to use a liveCD to partition--in fact, you can use the Ubuntu live CD. It has gparted already on it (at least the 6.06 disk does, have not tried the 6.10 disk). I have done this several times and it works great.

---

