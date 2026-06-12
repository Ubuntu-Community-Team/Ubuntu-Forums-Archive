---
title: "Imp[ortance of Swap"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Forrest319 on 2007-07-23
Last weekend I went ahead and installed Ubuntu 7.04.  I repartitioned one of my storage drives to create a 10 gig space to try things out on.  After I started going through the actual install process I was told that I should create a separate partition at the beginning of the drive for a page file.  Since I had just waited a long a$$ time while repartitioning my drive and told Ubuntu to proceed without one.

Now that I have been running the system for about a week I have decided that I want to keep it ( I actually have started XP since installing Ubuntu).  Would it be worth it to reinstall and create a swap partition?  I have noticed that programs seem to lose some responsiveness everyone once in awhile and thought that might be part of the reason.

I am running a gig of pc3200.  Thanks in advance.

---

### Post by armandh on 2007-07-23
with a gig of mem you probably do not need a swap file
most mem + swap installs are less than 1 GB any way.

---

### Post by forestpixie on 2007-07-23
All I can say is that with a gig of ram my swap is often used - not very much of it to be honest - but it does get used.  

So it might be worth it.

---

### Post by benx009 on 2007-07-23
> **Forrest319 said:**
> Last weekend I went ahead and installed Ubuntu 7.04.  I repartitioned one of my storage drives to create a 10 gig space to try things out on.  After I started going through the actual install process I was told that I should create a separate partition at the beginning of the drive for a page file.  Since I had just waited a long a$$ time while repartitioning my drive and told Ubuntu to proceed without one.

Now that I have been running the system for about a week I have decided that I want to keep it ( I actually have started XP since installing Ubuntu).  Would it be worth it to reinstall and create a swap partition?  I have noticed that programs seem to lose some responsiveness everyone once in awhile and thought that might be part of the reason.

I am running a gig of pc3200.  Thanks in advance.

unless you're really running low on disk space, i would create a swap partition.  just my recommendation.

you do not have to reinstall feisty at all to create a swap partition and have it up and running in no time.  you can use a [gparted]("http://gparted.sourceforge.net/") livecd, or, my personal pref., a [BootIt NG CD/Floppy]("http://www.terabyteunlimited.com/bootitng.html"), or even your feisty install CD to create a swap partition (any method will work).  then, when you start up your normal feisty install again, it should automatically detect it (I think).  if it doesn't, come back to the forums and post your /etc/fstab.

---

### Post by Forrest319 on 2007-07-23
Ok... I will probably go ahead and create a swap partition.  I'll probably just boot into Windows and use Partition Magic since I am familiar with it.  And I am pretty sure I can figure out how to make Linuz recognize the swap partition with the search function and these forums.

  Thanks for the suggestions.

---

### Post by xelink on 2007-07-23
on another note, with 2/4GB of RAM installed I never felt any performane issues with swap disabled.
unfortunately however, windows(or atleast photoshop, I'm often running out of swap space on that, nevermind the fact that I might have 2.5GB unused RAM) INSISTS on having pagefiling enabled, so I have to have some degree of pagefiling on that POS.


FYI I'm not sure if partition magic can make swap aprtitions. I know dang well however that the learning curve for gparted is almsot non-existant(atleast if you have some degree of knowlege about computers which you evidently do)

---

### Post by bodhi.zazen on 2007-07-23
> **Forrest319 said:**
> Ok... I will probably go ahead and create a swap partition.  I'll probably just boot into Windows and use Partition Magic since I am familiar with it.  And I am pretty sure I can figure out how to make Linuz recognize the swap partition with the search function and these forums.

  Thanks for the suggestions.

NOOOOOO

No need for partition magic. Boot the Ubuntu CD and fire up gparted.

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)


Time to break the addiction on closed source apps ;)

---

### Post by prabbit237 on 2007-07-23
You can create a swap file without even needing to touch the partitioning. It's not quite as efficient as a swap partition (especially if the partition is on a different drive/IDE controller) but with 1gig ram, you probably won't be using the swap that much anyways. Also you're limited on how many partitions you can create total and if you're dual-booting several OS's, you don't want to use the partitions up too quickly.

The one consideration, however, is fragmentation. If it's is a pretty new OS install, the free space on the drive will be pretty much contiguous and the swapfile will be pretty much in one piece. But adding a swapfile to a drive that's had years of usage would result in one that's in several chunks and will thrash the drive more (a swap partition can't be in pieces so that's one advantage to it.)

Take a look at [http://ubuntuforums.org/archive/index.php/t-265051.html](http://ubuntuforums.org/archive/index.php/t-265051.html) and it has info on creating a swap file and mounting it, etc.

---

### Post by bodhi.zazen on 2007-07-23
> **prabbit237 said:**
> You can create a swap file without even needing to touch the partitioning ... 

Good advice, thanks.

---

