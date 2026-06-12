---
title: "problem with partitions"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by KevNice on 2007-12-01
When I first installed Ubuntu, it asked me to select how much to devote to each partition. My laptops hard drive is 160 GB. I wanted to give 85-90% of the space to Ubuntu, and 10% to Windows.

I selected it and thought it was fine, but it turns out that I accidentally put the 85-90% in Windows (Vista) and only 10-15% to Ubuntu. 

Is there a way I can change this allocation without wiping the disk or re-installing?

Any advice is appreciated.

Thanks

---

### Post by forestpixie on 2007-12-01
Apparently it's best to use the vista partition tool. You can use gparted on the Ubuntu livecd. or get the gparted livecd to do the same.

---

### Post by KevNice on 2007-12-01
is that on the install CD? Do I have to boot off the CD to use it? Could you give me a quick walkthrough? Im kind of a noob and i dont want to f it up too bad

---

### Post by KevNice on 2007-12-01
ok, I tried to use the Vista repartition tool. There was over 100 GB of free space on the Vista partition, but it would only let me cut off around 45 GB maximum; and then it would not allow me to add that extra to the partition that I have Ubuntu installed on.

Any help?

---

### Post by ronmarley1 on 2007-12-01
I'm not that familiar with Vista and the partitioning tool, but I would download the gParted LiveCD and burn the image to a CD and boot that and make the changes.  From what I've read, you should only use the Vista partitioner to manipulate a Vista partition.  Don't use gParted on Vista.  The Ubuntu LiveCD will also allow you to used gParted, but I like the gParted LiveCD better.  That should allow you to add the freed space to the Ubuntu partition.

Get the gParted LiveCD here: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by bingoUV on 2007-12-01
> **KevNice said:**
> ok, I tried to use the Vista repartition tool. There was over 100 GB of free space on the Vista partition, but it would only let me cut off around 45 GB maximum; and then it would not allow me to add that extra to the partition that I have Ubuntu installed on.

Any help?

 It helps if you defragment the partition before trying to shrink it.

---

### Post by forestpixie on 2007-12-01
I've read here problems with not using the vista partition tool at the pre-install stage, I would assume that it'd be best to use that tool to do the shrinking - then you could use the gparted livecd to do the resizing of the ubuntu partition.

If I'm just repeating stuff from other threads that is outdated it'd be good to know, then I can forget about that - only been into vista 2 times - I jumped ship at the win2k stage (even if it was in 2007 ) .

---

### Post by KevNice on 2007-12-01
Ok I just used Gparted and formatted all the space that was being used by Windows to ext3. 
So no more Windows but 130 GB more free space!

only error seems to be that there is still about 1.3 GB of space that is unallocated and that I cant resize to any other partition. Im guessing its because I didnt defrag first

---

### Post by KevNice on 2007-12-01
ok im having a new problem, and that is it doesnt seem to allow me to write to the new partitions I made. They appear on my desktop as disk and disk-1 respectively, I can open them but not open any new folders in them. Do I need to chmod them or something first?

---

### Post by KevNice on 2007-12-01
bump

---

