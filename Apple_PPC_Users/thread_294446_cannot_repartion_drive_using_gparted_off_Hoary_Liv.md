---
title: "cannot repartion drive using gparted off Hoary Live CD"
date: 2006-11-06
forum: Apple PPC Users
---

### Post by fisherdmin01 on 2006-11-06
I'm trying to repartition my drive on my Lombard PowerBook G3.  I initially installed Ubuntu because I could not install OS X on this particular drive (an older, smaller one worked just fine.)  OS X installer could never find a destination drive to install to.

I have booted from a Hoary Live CD (I cannot get a burned iso to boot on the PowerBook (and YES, I DO know how to burn an iso)) and attempted to run gparted to ge me space for a HFS partition.  Gparted shows 4 partitions - a zero byte unrecognized partition, a 1MB unrecognized boot partition, a 733 MB Linux Swap partition and and 37 GB system partition.  When I attempt to resize the partition, I get a message that the disk is busy, the kernel doesn't like that, and I should reboot.  I don't understand as I am running off the Live CD.

I'm running Edgy, but as mentioned above, cannot get a burned CD to boot and the last shipit disk I received is Hoary.

Questions - how do I get gparted to work?  What are the 2 unknown partitions and can I delete them?

Thx in advance .....

---

### Post by ReaderRat on 2006-11-06
Are you using the most current gparted Live CD?
[**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php)

---

### Post by fisherdmin01 on 2006-11-06
I'm sure I'm NOT using the most current.  I'm using the Hoary Live CD. The link in your posting at Sourceforge indicates that gparted live cd is a x86-only distro.

---

### Post by Kalvin on 2006-11-06
The LiveCD (at least starting with Breezy...) will use Linux Swap space if it is available -- since that partition is in use, the partitioner will say the drive is busy.

There's the problem, but I don't have a solution for you.  Anyone know how to prevent the LiveCD from using the existing swap?

---

