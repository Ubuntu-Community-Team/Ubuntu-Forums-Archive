---
title: "Disk Partitioning"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by DSdragondude on 2007-08-05
I'm trying to make a disk partition so I can put Ubuntu on to my PC, I've tried following the Disk Partition topic in the Help and Support window of my current OS (Windows XP) but it says to right click on a free space to create a new partition. In short it won't let me right click so I can't create the disk partition, thus I'm not able to put Ubuntu onto my PC.


So can I fix this or is there another way around this?

---

### Post by PinkBullets9 on 2007-08-05
I am not sure that you can partition a disk after there are OS's installed on it but you could install Wubi and have Ubuntu installed on your Windows hard drive.

---

### Post by joe.turion64x2 on 2007-08-05
The Ubuntu liveCD is very handy in partitioning matters. Just open Gnome Partition Editor within it (it is in the System -> Administration menu) or in a terminal: *sudo gparted*

That program can do almost anything: resize Windows's NTFS partitions, move partitions around, create new ones, etc.

Joe.

---

### Post by lgambett on 2007-08-05
Yes, you can create a partition to put Ubuntu on your PC. I suppose you have Windows installed.
This is the procedure I always follow;
1) Defrag the disk with Windows defrag
2) Run chkdsk inside Windows
3) Download a copy of Knoppix, that is a very good live distribution ([www.knoppix.org](www.knoppix.org)) and burn it on a CD
4) Start your PC with Knoppix. Inside Knoppix you will find Qtparted, a partition utility like Partition Magic. Use it to resize your Windows partition.
5) Install Ubuntu on the free space you generated. At the end you will have a dual boot PC.

It is long, but it works and it is safe.

---

### Post by fatsheep on 2007-08-05
There is also [GPARTED LiveCD](http://gparted.sourceforge.net/livecd.phpt[/url) if you want.  It hasn't failed me so far. ;)

---

### Post by Sbarton on 2007-08-05
For dual booting see this: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) If that is not the page you want see other pages.
regards

---

### Post by pablo66 on 2007-08-05
I have used the Ubuntu 7.04 Live CD to load up a dual boot mochine several times with no problems.  I always install windoze first(it will wipe out the linux install if you do it the other way around), then boot to CD and click on the 'Install' icon when Ubuntu loads up.  Go through the setup and it will come to a disk resizer that will allow you to allocate a partition size and keep your other OS intact and then it will partition it automatically from there.

---

