---
title: "Reclaim Hard Disk space"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by copperco2 on 2008-02-09
I had XP loaded before i installed ubuntu on it. I did not do any formatting before installing it.
now the system information shows the total disk space as 35.3GB instead of 40GB as it should.

Is there any windows component occupying the Hard Disk and can not be seen....

if it is so, how can that be rectified?

Ubuntu and components are using 2.1GB of space..

---

### Post by tom66 on 2008-02-09
The 40 GB is probably talking about 1,000 bytes, while the 35 GB is probably talking about 1,024 bytes. It makes a lot of difference with large files. 

There's nothing you can really do.

---

### Post by fiddledd on 2008-02-09
> Ubuntu and components are using 2.1GB of space..

There's also some space used for the Journal in EXT3 and I think some space is reserved so you can't run out of disk space. So it may be correct to lose a few gb.

---

### Post by randy78 on 2008-02-09
I have a 200GB Hard-Drive, but the true available space is only around 180GB, even when it's completely blank...

It's kind of shady, but that's how it's always been... a lot of companies sell 180 GB drives as 200GB drives, even though they aren't truly 200GB.

For a 40 GB Drive, you've probably got a real storage capacity of around 36GB.

Hope that explains it.

---

### Post by smacattack on 2008-02-09
I have a 40GB drive and in my case.. it only shows 35GB or something because of extra partitions by Dell as recovery or whatever. It could be hidden partitions by your vendor.

---

### Post by NightwishFan on 2008-02-09
Ext3 uses 5% of your space to reduce the need to defragment.

---

### Post by copperco2 on 2008-02-09
But when i had windows, C and D drives were divided into 20GB each, and it showed that way..

how was that possible.?

---

### Post by Paqman on 2008-02-09
> **smacattack said:**
> I have a 40GB drive and in my case.. it only shows 35GB or something because of extra partitions by Dell as recovery or whatever. It could be hidden partitions by your vendor.

If you suspect this you can check using Gparted. That will show all the partitions on your machine (hidden or otherwise)

The size discrepancy people were talking about is the difference between a [gigabyte](http://en.wikipedia.org/wiki/Gigabyte) and a [gibibyte](http://en.wikipedia.org/wiki/Gibibyte). They're used kind of interchangeably a lot of the time, and it creates confusion.

---

