---
title: "[SOLVED] entire disk unmounted yet working"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-12-06
Like the Mad Hatter in Alice in Wonderland . . . the hurridier I go, the behinder I get.

I have or had 2 hard disks. There is no M$ anywhere near here as Mr. Gates and I are no longer speaking to one another.

The "original" hard drive (20 gig), sat as primary-slave. Everything worked fine. I bought a new hard drive of 320gig. The 320 sits as cable-select primary-master.

I used G4L (formerly Ghost 4 linux) to "clone" the 20 gig to the 320 gig. It made a perfect copy. All the user names, passwords, i.d., things Firefox remembers were there along with Google Earth's icon on the desktop.

I spent most of this week trying to change the sda1 from about 15gig to 287gig. No luck. 

So here's the $64,000 question: WHY does GParted now show that none of the 320gig's partitions are mounted? And if they aren't mounted, how is it possible that I'm using the disk at all?

Ideally, I want to increase the /home's available space to max, remove the old 20 gig and add a 40gig that has a /home I want to "rename" and move it's /home files to the 320 gig. But 1st things 1st. How is it possible to have no disk mounted and a "working" computer?

---

### Post by Therion on 2007-12-06
Maybe I'm confused and not understanding what you're asking, but in your first screenshot it appears sda is your 320GB drive.  I see three partitions: Partition 1 at 13.6GB, Partition 2 (the "swap" partition) at 1.9GB , Partition 3 at just over 2GB and lastly, a huuuuuge chunk of unpartitioned, unallocated, drive-space, sda4.  

Assuming sda1, sda2 and sda3 comprise the "ghost" image you copied from the old 20GB hard drive, this is pretty much what I would expect to see:  You copied not only the data from the old drive to the new drive, but also the partitions which were also applied to the new drive.  

I think what you want to do, most likely, is use that unallocated space for Ubuntu, correct?  If so, I think what you need to do is partition the unallocated space, and then merge it with the existing (13.6GB) partition.

---

### Post by Mark_in_Hollywood on 2007-12-06
Help came from another post:

[http://ubuntuforums.org/showthread.php?t=633636](http://ubuntuforums.org/showthread.php?t=633636)

---

