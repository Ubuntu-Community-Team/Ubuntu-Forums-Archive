---
title: "Partitioning Question"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by sarcazmo on 2007-05-06
I've been speaking to confused57 (bless him!) about installing Ubuntu and dual booting it with XP on my machine.  I was really hoping I could use the ubuntu installer to create the partition from the excess space on my windows drive.

However, I ran the sudo fdisk-l command at confused reccomendation and came up with this ```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 6 48163+ de Dell Utility
/dev/sda2 * 7 9333 74919127+ 7 HPFS/NTFS
/dev/sda3 9334 9725 3148740 db CP/M / CTOS / ...
```

Apparently dell created a couple other partitions on my drive already!  When I tell the installer to create a new partition from the largest continuous space, it says the space is too small.  I'm thinking thats because its looking at the sda1 partition.  Is there any way to make it look at the sda2 partition?

---

### Post by alienexplorers on 2007-05-06
A lot of computers come with a partition that contains a re-install program for windows instead of giving you a re-install disk.

---

### Post by rygar on 2007-05-06
when it says "use largest continuous free space", that means *unpartitioned* space (or rather, space that isn't allocated to a particular filesystem).

the installer isn't "looking" for free space in sda1, or sda2 or sda3 for that matter.  even if your XP partition has 50 free gigs, that space is formatted to NTFS (Windows format), and allocated for Windows to use.  you cannot install Ubuntu on there.

you're probably going to have to resize your XP (/dev/sda2) partition, and make it smaller.  i don't know if the installer does this for you, i've only installed Ubuntu once.  if you boot from the Ubuntu cd and go into the partition editor (system -> administration), you may be able to shrink your partition.  make sure you have plenty of free space in this partition!

---

### Post by rygar on 2007-05-06
one last note:  unless you're 100% confident in what you're doing, messing with your partitions carries certain risks.  make sure to back up any important data where possible!

---

### Post by Malta paul on 2007-05-06
Run your live Ubuntu disk, then check the hard disk partitioned free space using System>administration>Gnome Partition Editor. This will give a graphic picture of your existing partitions and how full they are.

As Rygar  said please be careful, backup and go slowly. This link may help you, good luck :) [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

---

### Post by antoz on 2007-05-06
I am pretty sure if you select the largest free space it will pick the largets partition and resize it, you will get a screen with a slider and partition size What you see there is what your existing partition will be left with not the new one, so you can move it till you are happy with the size. A much better way would be to edit your partition table first with the Gnome partition editor provided there is enough space (defrag first) simply resize and create new partitions in the unallocated space.
Ideally you should create 3 partitions:
one for "/" this is where Ubuntu goes
one for "swap" about 1.5 time your ram
one for "home" not neccesary but better if you need to reinstall later you keep all your files and settings intact.

here is another good link: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

