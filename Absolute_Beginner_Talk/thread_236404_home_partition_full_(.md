---
title: "home partition full :("
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2006-08-14
Hello,

When I installed Ubuntu, I took the advice of some linux guru somewhere on the web (can't remember where at this moment), and partitioned my 40GB drive as follows:

5GB Windows
25GB FAT 32 (for mp3s, etc)
1GB Home Directory
9 GB Linux

Of course, now my home directory is out of space.  Is there any way to fix this without wiping out my data?  Have I made a newbie partitioning blunder?

Thanks for your help!

---

### Post by siacs on 2006-08-14
You can use GParted to resize your partitions without too much risk. Backup anything very important first. There are limitations though.

General information
[http://en.wikipedia.org/wiki/GParted](http://en.wikipedia.org/wiki/GParted)

The main site
[http://gparted.sourceforge.net](http://gparted.sourceforge.net)

The LiveCD to do the resizing
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by djsroknrol on 2006-08-14
It might not be possible...it depends on how your partitions are set up...could you post a screenshot, and someone might be able to tell you better...

---

### Post by az on 2006-08-14
> **limberlegs said:**
> Hello,

When I installed Ubuntu, I took the advice of some linux guru

Smartass linux gurus piss me off.  All-on-one partition is what I reccommend.

> **limberlegs said:**
> 


A- 5GB Windows
B- 25GB FAT 32 (for mp3s, etc)
C- 1GB Home Directory
D- 9 GB Linux

You cannot shrink or move from the begining, only from the end of a partition.

I added letters to your partitions above:

If you want five more gigs for home, shrink B by five gigs.  Then move C to the beginning of the free space.  Then extend C to go to the end of the free space.  

Be sure to extend the filesystem as well as the partition when you do that.  Gârted usually does that for you, though.

---

### Post by limberlegs on 2006-08-15
Thanks to all for your replies!  I have backed up my files with a USB drive, and will atttempt to do some re-partitioning with a little more foresight.

I guess I just don't quite understand the linux filesystem just yet.  What, exactly, is the home directory used for?  What gets installed there?

Also, could I do something like this:

1GB allotted to /home/
1-2GB allotted to /home/user/personal-data

Where "personal-data" would be a directory that contains all of my personal files (papers, etc).  Right now, my "personal-data" takes up approximately 1GB, which is why my home directory filled up in the first place.  

Thanks for all of your help!

---

### Post by az on 2006-08-15
> **limberlegs said:**
> 
Also, could I do something like this:

1GB allotted to /home/
1-2GB allotted to /home/user/personal-data


Yes, but what a mess!

---

