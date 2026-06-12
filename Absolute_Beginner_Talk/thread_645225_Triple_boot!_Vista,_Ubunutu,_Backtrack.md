---
title: "Triple boot! Vista, Ubunutu, Backtrack"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by jainsy on 2007-12-19
Hi all,

First off i am new to Linux but so far have been very impressed with Ubuntu and the support offered here on the forums. I've had many a problem and a simple search in these forums reveals all answers!

However,
I am trying to do a dual boot of Vista, and two linux operating systems, Ubuntu and backtrack 2 ([http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)).
I already have vista installed on a partition of 70 gig have another partition for formatted as ext3 of 30 gig intended for Ubuntu and another 12 gig formated as ext2 for Backtrack 2 (ext2 is required).
I thought it best to install Backtrack 2 next as the boot software with Ubuntu seems to be best and recognizes other OS's already installed. 

My partition setup is as below (according to Ubuntu installer)
device      type  mount point
/dev/sda1 ntfs   /media/sda1
/dev/sda3 ext3  /media/sda3
/dev/sda4 ext2  /media/sda4
/dev/sda5 swap
/dev/sda6 swap

I assume I only need one linux-swap partition? (For some reason I have two..)
When trying to install ubuntu to sda3 it says no mount point is set, what do i do?

Any help appreciated,
Many thanks!

---

### Post by Moop on 2007-12-19
You need to have a mount point of / to install to. Just change the mount point from media to / on the partition you want to install to.

---

