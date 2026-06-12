---
title: "No yaboot partition?"
date: 2011-03-01
forum: Apple Hardware Users
---

### Post by skinnie on 2011-03-01
Hi guys, I am trying to install either ubuntu or debian in my powermac, although when making partitions it gives this error:
> No NewWorld boot partition was found. The yaboot boot loader requires an Apple_Bootstrap 
partition of at least 819200 bytes in size, using the HFS Macintosh file system.

What should I do?I have my hdd partitioned with the MacOS 10.4 Dvd (install MacOS 9 drivers enabled - if that matters) like this: 40Gb Tiger,50Gb Leopard,20 Gb "Free Space" (for linux) and the rest as "Data" in HFS.

What should I do to make it work?
Thanks

---

### Post by linuxopjemac on 2011-03-01
you have to make the first partition (1MB) Apple bootstrap. It has to be within a certain limit, I am not sure how much.

[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

---

### Post by dbrooke on 2012-03-13
I'm getting the same Error as this original poster.


Installing Ubuntu Server Lucid Lynx 10.0.4 PPC, on an old iMac.

I'm in the "Partition Disks" section of the install.. anyone know how to create an Apple_Bootstrap partition, in HFS?

Thanks
Donovan

---

### Post by dbrooke on 2012-03-13
Well, in the case someone else finds this.. here is what I did (and I am not sure it is correct).

I could not get free of the Apple_Bootstrap error using:

guided - entire disk using LVM (paraphrasing)

So, I first did a:

guided - use entire disk

I then highlighted the free space and clicked on it to create a partition. 
 - size is 1 MB.
 - set it to be at the "beginning" of the partition scheme

 - named it Apple_Boostrap
 - type of use is "Newworld Boot <something>" (no HFS format options)

 - highlighted and entered to save.

That took me back to the main partition page.

I then highlighted the remaining free space and hit enter to partition the remaining space.

I selected "automatically create partition".

This created the swap and root partitions for me.

Continued with partitioning and no error.

I hope that is correct. ;-)

Donovan

---

