---
title: "Partitioning Software"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-19
Hey there, I was always using partition magic when I was in windows. Now, since I've deleted my windows partition I have 20gb's just sitting there, what I'd like to do is merge that into my linux and let my whole hard drive then be sole linux. I mean I'm only running Ubuntu now but I want to make sure that my whole hd is Ext3. Any good partitioning software out there for ubuntu? Thanks! :)

---

### Post by aysiu on 2007-05-19
GParted
QTParted

---

### Post by Outrunner on 2007-05-19
I highly recommend [GParted LiveCD]("http://gparted.sourceforge.net/download.php"). Very good, very useful.

---

### Post by ugm6hr on 2007-05-19
Try GParted (aka GNOME Partition Manager).  It will look familiar (and is free).

In order to merge with the Ubuntu boot partition, you will have to boot from CD (i.e. not from the partition involved in resizing).  Best option is to get a fresh copy of the GParted Live CD:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

When you boot from it - generally best to select the second boot option, otherwise no hardware seems to work.

---

### Post by Marsolin on 2007-05-19
While both appear to be pretty similar, I've found [GParted]("http://linuxappfinder.com/package/gparted") to be more capable that [QTParted]("http://linuxappfinder.com/package/qtparted") in manipulating existing partitions. And I'm a KDE user who was initially more inclined to use QTParted.

---

### Post by laidback on 2007-05-19
Gparted, either from Ubuntu Live CD or better still download the Live version which in my opinion is a better version. Don't forget that you cannot alter a mounted partition, hence the need to boot into another system.

---

### Post by maniacmusician on 2007-05-19
I think QTParted is bit obsolete? It's website shows that it **hasn't been updated since 2004**. GParted is much more up to date, so please don't use QTParted.

---

