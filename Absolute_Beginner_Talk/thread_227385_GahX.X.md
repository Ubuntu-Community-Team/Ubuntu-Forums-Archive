---
title: "GahX.X"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by blajah on 2006-08-01
Ok, I'm completly new to Linux(hence why I am in the Begginers forum and askign a question^_^), I have used Windows for the last few years, and I have not yet installed Ubuntu.
I just this morning got the package with teh free Ubuntu cd's, and booted up the 64-bit pc version(running a 64-bit AMD PC).

I've looked around and read the installation wiki abck to front, but I still can't find an answer.

My question is this:
I have two Hard drives in my PC. One is a 20gig, the otehr is a 200gig.
The 200 gig is partitioned(in Windows) to be a 120 and a 80 gig. I dont want to touch either of these drives as they have all the info i wanna keep.

The 20 gig is split into a 10gig which has my major Windows Drive, and the rest is currently unpartitioned space.

How do i manually set up Ubuntu so that it installs only in this unused space? When i run the isntaller it asks me to make multiple partitions and such, and Im comp[letly lostx.x

Thanks for listening and hopefulyl replying very fastXD!
-Blah-

---

### Post by ironfistchamp on 2006-08-01
Erm I think when running the installer you would go to manually edit partition table, select the correct disk and then make a new partition in the unused space. I use ReiserFS for my Linux partition. Anyway when that is done hit next and it will ask you where you want to mount each partition. Look at the options and select the new partition to be mounted at / (which means root).

I hope I was clear in my explanation.

---

### Post by blajah on 2006-08-01
> **ironfistchamp said:**
> Erm I think when running the installer you would go to manually edit partition table, select the correct disk and then make a new partition in the unused space. I use ReiserFS for my Linux partition. Anyway when that is done hit next and it will ask you where you want to mount each partition. Look at the options and select the new partition to be mounted at / (which means root).

I hope I was clear in my explanation.

Ug, but when I do that it tells me I need to have more then one partition, and tries to get me to put files like /media/hdc in the second hard drive I had, and wont let me jsut make a /(root) partitionx.x

~lost~

---

### Post by ironfistchamp on 2006-08-02
I think I understand. It is trying to mount the other partitions you have. I won't delete or add anything it is just making it possible to view other partitions from Linux. Just leave then all mounted at /media/hdX. Make sure you untick reformat if it is ticked otherwise you will loose data.

---

