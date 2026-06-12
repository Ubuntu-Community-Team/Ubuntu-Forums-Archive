---
title: "Quick install question"
date: 2008-09-22
forum: Apple Hardware Users
---

### Post by linuxlizard on 2008-09-22
My wife just got a new macbook 4,1 at work and we'd like to partition the hard drive and dual boot into ubuntu. I was reading an install guide and it said that the drive had to be partitioned before installing osx or we'd loose it because for some reason resizing the partitions and partitioning reformats the drive and wipes it clean, unlike windows.

Is that still correct? My wife did not receive an install disk with the system, and we really don't want to have to run through the red tape to get one and explain what ubuntu is and why we are installing and how it won't destroy her computer, etc...

Or is it possible to resize her osx partition and add another one for ubuntu without destroying osx that's on there now?

Thanks much!

---

### Post by cyberdork33 on 2008-09-22
> **linuxlizard said:**
> My wife just got a new macbook 4,1 at work and we'd like to partition the hard drive and dual boot into ubuntu. I was reading an install guide and it said that the drive had to be partitioned before installing osx or we'd loose it because for some reason resizing the partitions and partitioning reformats the drive and wipes it clean, unlike windows.
No. Use bootcamp or diskutility in OSX to partition the drive. you can 'add' another partition to the hard drive. Ten after that, you can boot the Ubuntu LiveCD and change the new partition to free space in Gparted and install ubuntu using "the largest continuous free space".

> **linuxlizard said:**
> Is that still correct? My wife did not receive an install disk with the system, and we really don't want to have to run through the red tape to get one and explain what ubuntu is and why we are installing and how it won't destroy her computer, etc...

Or is it possible to resize her osx partition and add another one for ubuntu without destroying osx that's on there now?
You can also just resize your HFS+ (OS X) partition with gparted, but I would recommend using the Apple tools if you can.

P.S. Intrepid has a lot of fixes for the Penryn MacBook Pros, I would just go ahead and install it (or wait for the final release).

---

