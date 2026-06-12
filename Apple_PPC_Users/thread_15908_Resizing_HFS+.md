---
title: "Resizing HFS+"
date: 2005-02-17
forum: Apple PPC Users
---

### Post by pherthyl on 2005-02-17
Hey,   I have an older iBook (500Mhz, 384MB RAM) that I wanted to install ubuntu on alongside of OS X.

I have quite a bit of Linux experience (been running Debian for the past 3-4 years on my x86 box) but have never tried it on a PPC.  

So the problem is that OS X (10.3.8) is now using the whole hard drive (39GB).  I booted into the Ubuntu installer from CD and it looked like it was going to let me resize my HFS+ partition.  I bailed out when it wanted to write something to the partition table before resizing.  I know the new parted supports HFS+ resizing but I havent heard anything about the Ubuntu installer.  
Does anyone here have any experience with resizing HFS+ from the ubuntu installer?  Does it work?  Is it reliable?  I really really don't want to wipe OSX and reinstall.  Too much of a pain :)

Thanks, 
leo

---

### Post by farmer on 2005-02-18
I don't think you can resize HFS+. I tried to when I first got my mac, but it destroyed all the data on it.

---

### Post by pherthyl on 2005-02-18
Hmm..   Perhaps I can boot a liveCD of some sort with GNU parted on it to resize it...

---

### Post by ewaldgroup on 2005-02-19
I did exactly what you want to do. Check out iPartition, it does a wonderfull job, even if it takes a bit too long to do it.

[http://www.coriolis-systems.com/iPartition.php](http://www.coriolis-systems.com/iPartition.php)

-ewaldgroup

---

### Post by pellix on 2005-02-22
I think that you can do it with a Gentoo Minimal live-cd, for example: [http://ftp.belnet.be/mirror/rsync.gentoo.org/gentoo/releases/ppc/2004.3/livecd/install-ppc-minimal-2004.3.iso](http://ftp.belnet.be/mirror/rsync.gentoo.org/gentoo/releases/ppc/2004.3/livecd/install-ppc-minimal-2004.3.iso)
 
But I'm not sure about resizing HFS+, sorry.

---

### Post by chascon on 2005-02-26
debian sarge d-i resizes HFS+, non-journalled.  Just disable journalling in OS X prior (you can reenable it after resize).  I think it was parted that does this, and you have to go into "advanced install mode" when starting th d-i

---

### Post by robzulah on 2005-03-04
I'm having almost an identical problem, except I'm stuck with mac OS 8.9.  I cant find any software to let me resize the partition that will work for my poor old OS.  Anyone know of anything?

---

### Post by theturner on 2005-03-24
[FWB Partition Toolkit](http://fwb.com/html/partition_toolkit.html) works with Mac OS 9.1 to 9.2.x. It's commercial, and you have to pay US$ 25 for it. I got a used copy, but i'm stuck anyway, because it won't resize the Mac OS startup disk, which is my only partition, and my Mac is a Wallstreet, so it won't boot the Ubuntu CD.
So, does anyone know whether there's a way to burn an image of my OS 9 plus Partition toolkit to CD and select the CD in the startup disk control panel?

---

### Post by closet geek on 2005-11-13
[QUOTE=ewaldgroup]I did exactly what you want to do. Check out iPartition, it does a wonderfull job, even if it takes a bit too long to do it.

[http://www.coriolis-systems.com/iPartition.php](http://www.coriolis-systems.com/iPartition.php)

-ewaldgroup[/QUOTE]

How many people have had success with iPartition? Does it work as you'd expect, was there any data loss, what steps did you take etc?

cg

---

