---
title: "[SOLVED] Will the filesystem be damaged if there is not swap?"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-11-30
Trying to change the partition sizes with GParted, this happened:

grub> geometry (hd0)
drive 0x80: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83


Gutsy boots OK and shuts down OK, I'm online OK, so do I need to add a partition? I have a gig of ram and set swappiness from 60 to 10, anyway.

---

### Post by Drate on 2007-11-30
I don't think your filesystem would be damaged, but it is a good idea to have a swap.

---

### Post by lespaul_rentals on 2007-11-30
I know people who don't have a swap.  It's not too bad, so long as your RAM doesn't fill up.  You probably want one, though.

---

### Post by Mark_in_Hollywood on 2007-11-30
On the "fly" I have made a 1.9GiB partition, and allocated it as linux-swap. Will this satisfy the system requrements?

See attached thumbnail.

Also, why does the exclamation sign say the disk has no "mount point"?

---

### Post by quandary on 2007-11-30
> **Drate said:**
> I don't think your filesystem would be damaged, but it is a good idea to have a swap.

Not as long as there is no need to swap files outside ram.

If however you need more ram than you have, the system will swap to the temp directory in your ext3 partition. If the system for example crashes meanwhile, it can damage your ext3 partition, which can be a problem.

If the system swaps on a swap partition, only that partition would in case be damaged, but there is no data on it, so you could just repartition in that case, without loosing data...

So, i conclude, using a seperate swap partition is a little bit more secure, however, not that much ;-)

---

### Post by Mark_in_Hollywood on 2007-11-30
Yes, I see, but that's not much in the way of an answer about the "no mount point" stuff.

---

### Post by Drate on 2007-11-30
Oh, yes, it looks like you've done it.  I think the rule of thumb for swap partitions is 1.5 times your RAM... or was it 2.5?  something like that.  Anyhow, that's just convention, not necessary, eitherway, you have yourself a swap, your life will now be INSTANTLY BETTER!  Okay no... but possibly a slice more secure.

---

### Post by Sef on 2007-11-30
> I think the rule of thumb for swap partitions is 1.5 times your RAM... or was it 2.5? 

Rule of thumb for swap is 1.5 time your ram.   However, once you get 2 gb or more of ram, then swap is not really necessary, unless you do some heavy gaming or movie editing.   With 1 gb ram, I would have a swap of 1 gb.   You should not have any problems with that set up.

---

### Post by Mark_in_Hollywood on 2007-12-07
I'm not much of a "hand" with partitioning and doing the "guts" work, but I was able to make a swap partition using LiveCD GParted. GParted had to be "manually" started with 

cd /bin

./Forcevideo

and I had to enter nv (for nVidia cards) and a default return for 1024x768. After that, if worked well enough and I created a 2 gig swap, which is 2x my memory. When GParted was done, the actual size was 1.9gig.

I'm marking this post solved.

---

