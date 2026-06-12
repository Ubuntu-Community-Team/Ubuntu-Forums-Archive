---
title: "Partition Trouble ( Wrong Sizes )"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2008-03-22
When I was installing Ubuntu 7.10 , I went through the steps of partitioning my drive.
I chose to manually partition because I wanted a certain partition scheme. I set up my
partitions like this....

80 Gig drive

15 Gigs:   /
24 Gigs:  Home
1 Gigs:    Swap

Rest is free space

Well, after the formating and installation process, I noticed my partitions were incorrect. 
I went into System Monitor and saw that my / partition was 13.8 Gigs and my Home was 
2.2 Gigs.  Anyone know why this happened? Is this kinda thing common and happens 
sometimes?  

Should I start all over and reinstall or is it just showing the numbers wrong in System Monitor 
and I really do have a 24 gig partition for the home partition?

Is there a way I can look at the partitions with something like Gparted or command line?
I'd like to find out if I really have 24 gigs for the home partition.

Thanks

---

### Post by cotcot on 2008-03-22
I can recommend the [[COLOR="black"][COLOR="Red"]GParted LiveCD[/COLOR][/COLOR]]("http://gparted-livecd.tuxfamily.org/").

I always use this CD to arrange my partitions before installing an OS. 

You do not need to reinstall you OS. The Gparted LiveCD allows you to inform,  move and resize the partitions easily. When you use it I recommend to do only 1 modification, then execute it and then the second modification etc. It is not necessary but it is a good attitude in prevention of risks.

---

### Post by spupy on 2008-03-22
Well, could have dropped out a digit when entering the partition size from /home? Also, do know that there is confusion between gigabyte(GB) and gibibyte(GiB), especially when it comes to harddisk space. That could explain the size of your root partition.

---

### Post by Orbital75 on 2008-03-22
You know, I think that's what I did......  I think I entered in 2400 by mistake....
:)  I shouldn't have been in a hurry...

---

### Post by spupy on 2008-03-23
Entering "df" in a terminal will show the sizes of your partition in bytes. One have to enter partition size in bytes in the installer, if I recall correctly?

---

