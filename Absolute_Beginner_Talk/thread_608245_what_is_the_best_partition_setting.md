---
title: "what is the best partition setting?"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-11-09
Hi,
I am about to reformat my machine. currently I have lots of partitions on my harddisk but I am not sure whether partitions are optimized. I have 30 GB hard disk and I have the following partitions:
/                  :2.8 GB
/boot            :89 MB
/home          :13 G
/tmp             :897 MB
/usr              : 8.7
/var              :1.4 GB

is it good or bad having many partitions? How many partitions do you create? How big are they? How many partitions would you create if your computer has only 30 GB hard disk?
Thanks...

---

### Post by oilchangeguy on 2007-11-09
> **mozkaynak said:**
> Hi,
I am about to reformat my machine. currently I have lots of partitions on my harddisk but I am not sure whether partitions are optimized. I have 30 GB hard disk and I have the following partitions:
/                  :2.8 GB
/boot            :89 MB
/home          :13 G
/tmp             :897 MB
/usr              : 8.7
/var              :1.4 GB

is it good or bad having many partitions? How many partitions do you create? How big are they? How many partitions would you create if your computer has only 30 GB hard disk?
Thanks...

what's with all of the needless manual partitioning? just let the operating system pick it's own partitions.

---

### Post by gn2 on 2007-11-09
I use three partitions.
For a 30gb hard drive:

/ 6gb
/home whatever's left.
swap 1.5xRAM up to a maximum of 1gb

There isn't a "best" partitioning scheme any more than there's a "best" distro, but that's what works for me.

---

### Post by Orbital75 on 2007-11-09
Yeah, all the partitioning is a waste of time....  All you really need to do is this

/
Swap
Home

Some would say you don't really need to have a home partition but if you want to
reinstall Ubuntu in the future it will help by separating your OS and Home.

---

### Post by mivo on 2007-11-09
I would go with:

/ = 8-10 GB
/home = everything else that is left after swap
swap = same as your RAM if you have 1 GB or more, 1 GB swap if less than 1 GB.

---

### Post by rsambuca on 2007-11-09
There is simply no benefit to splitting up everything into separate partitions like that.  All it will do is either waste disk space, which you don't have a lot of, or you will run out of space for one of the partitions and then run into problems that way.

Just a root, swap, and if you wish, a separate home.

---

### Post by Jittoku on 2007-11-09
Well, how do you estimate how much space you need for root?  Do you have to allow for new software and upgrades?  How much is enough?

---

