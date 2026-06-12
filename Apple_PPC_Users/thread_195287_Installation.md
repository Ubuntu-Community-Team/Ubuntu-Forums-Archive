---
title: "Installation"
date: 2006-06-12
forum: Apple PPC Users
---

### Post by VittorioCole on 2006-06-12
I've been running Ubuntu 5.10 on my PC for a while now, and i've really liked it, so when i heard about 6.06 for PPC, i downloaded my .iso, and made a cd, expecting to install it like i did on my PC. 

However, as i was going through the set up, it informed me that my hard drive was not big enough to house Linux, that it couldnt create partitions.

I'm running a 30 GB HDD, and i was looking to partition 20 GB to OS X and 10 GB to Ubuntu 6.06. (I'd like to dual boot, like i do on my PC)

Any suggustions? :confused:

---

### Post by acorn22 on 2006-06-12
Yes. Go here ( [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) ) download the cd and burn it. Then go here ( [http://www.gnu.org/software/parted/manual/parted.html#Using-Parted](http://www.gnu.org/software/parted/manual/parted.html#Using-Parted) ) and read how to use the program parted. (on the disk)

This program lets you edit your partitions without loosing data. basic rundown of what you'd do.

```
parted
resize (will prompt you for the rest of the information)

```

tips:
start is the point on hdd to start partition. so partition one would start at 0mb and end at 20 GB. partition 2 would start at 20 Gb and end at 30 gb.

I don't know if you need to create a new partition, since ubuntu gives you the option to install it in the open space, and it needs to create a swap space anyways...

BACK STUFF UP... of course

That's it :) You might want to try 'print' first to get a look at what's going on. (prints data to screen)

BE SURE TO READ THE GNU MANUAL (link i provided)

---

### Post by Ptero-4 on 2006-06-14
> 
Yes. Go here ( [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) ) download the cd and burn it. Then go here ( [http://www.gnu.org/software/parted/m...l#Using-Parted](http://www.gnu.org/software/parted/m...l#Using-Parted) ) and read how to use the program parted. (on the disk)

This program lets you edit your partitions without loosing data. basic rundown of what you'd do.

Code:
parted
resize (will prompt you for the rest of the information)

tips:
start is the point on hdd to start partition. so partition one would start at 0mb and end at 20 GB. partition 2 would start at 20 Gb and end at 30 gb.

I don't know if you need to create a new partition, since ubuntu gives you the option to install it in the open space, and it needs to create a swap space anyways...

BACK STUFF UP... of course

That's it  You might want to try 'print' first to get a look at what's going on. (prints data to screen)

BE SURE TO READ THE GNU MANUAL (link i provided)

Or you can use the QtParted util included in the CD.

---

