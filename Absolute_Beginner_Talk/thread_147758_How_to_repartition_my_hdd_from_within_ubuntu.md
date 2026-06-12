---
title: "How to repartition my hdd from within ubuntu?"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by wsantoso on 2006-03-20
Newbie ubuntu/linux user here. I installed ubuntu on my spare hdd the other days and so far so good. I want to create a new FAT partition on the hdd that I installed ubuntu on so I can share files between ubuntu and windows xp (on my main hdd). How do I repartition existing hdd to create a FAT partition in ubuntu?

Thanks in advance.

---

### Post by taurus on 2006-03-20
You need to use gparted for that.

---

### Post by dragomirov on 2006-03-20
Try installing gparted or qparted.

h&k

---

### Post by Sutekh on 2006-03-20
You can't use GParted *in* Ubuntu as the disc must be unmounted before you can partition it.  If you are running Ubuntu off the hard disc then it can't be unmounted.

I can think of three options to do what you ask, there may be more

1) Try [Disk Drake]("http://qa.mandriva.com/twiki/bin/view/Main/DiskDrake")

[Ubuntu Forums - Howto Use Disk Drake]("http://www.ubuntuforums.org/showthread.php?t=114142")


2) Try the [GParted LiveCD](http://gparted.sourceforge.net/livecd.php)


3) Try any LiveCD and GParted


The Disk Drake / GParted LiveCD / General LiveCD will allow you to run a system without using the hard disc so you can partition it.

---

### Post by wsantoso on 2006-03-21
Thanks Sutekh. I thought there was an easier way/command to do it from within ubuntu itself. Couldn't be bothered with having to burn additional liveCD so I downloaded and installed fs-driver on my XP instead.

---

### Post by Sutekh on 2006-03-21
Fair enough.  You know that the GParted LiveCD is less than 30MB?  You could probably even boot it from a USB device... which gives me an idea, something for later...

Anyway I don't know much about fs-driver, I have seen info floating around the forum relating to it though.  Good Luck!

---

### Post by WoodyMahan on 2006-03-21
I formatted my hard drive using: System -> Administration -> Disks

I chose the Hard drive I wanted to work on, Clicked on the Partitions Tab and Then Clicked Format.  I'm fairly new and don't know if this is just a graphical interface for gparted.  After formatting I had to back and mount the drive from the command line.  It doesn't do that from the GUI.

---

### Post by wsantoso on 2006-03-21
Woody, thanks for the reply. The partition I wanted to resize (split to create the FAT) was the one that Ubuntu was installed on so it was mounted as Sutekh pointed out. FS-driver is working so far to allow me to share files between the two OS.

---

### Post by Sutekh on 2006-03-21
[QUOTE=wsantoso]FS-driver is working so far to allow me to share files between the two OS.[/QUOTE]

Can I take this to mean that you have it working?

---

### Post by wsantoso on 2006-03-21
Yep, it was just a quick download & install and i can now read/write to my linux partition from xp. It's not ideal though as I don't want windows to have full access to the whole of that drive, but it will do for now until I can be bothered to do the gparted livecd thing.

---

