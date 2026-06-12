---
title: "Partitioning for a Dual Boot of OS X and Ubuntu 10.04 on PowerBook G4?"
date: 2010-05-18
forum: Apple Hardware Users
---

### Post by G33shooter on 2010-05-18
I originally posted this in a different thread I started, however, I feel this question is really separate from that original thread topic, so I decided to make this question part of a whole new thread.

Is it true with the ubuntu installer, you can choose to partition the  drive so that I can dual boot OS X and Ubuntu 10.04?  If I could dual  boot OS X and Ubuntu, would there be a screen when I turn on the comp  asking whether I want to boot into OS X or Ubuntu?  Also, assuming I  could partition my drive to have Ubuntu too, how many partitions are  needed for linux? Anyone have any screenshots/links/examples of a dual boot installation process? Also, what are the partitions called and how much space is needed for each?  

Here are my specs:

12" Aluminum PowerBook G4
Mac OS X 10.4.11
1.5 GHz PowerPC G4
1.25 GB DDR SDRAM
Macintosh HD:
Capacity:    74.41 GB
Available:    46.22 GB
Writable:    Yes
File System:    Journaled HFS+
BSD Name:    disk0s3
Mount Point:    /

Based on my specs, could you give me advice on how you would dual boot  OS X and Ubuntu and how you would allocate space for each partition  etc.?

Thanks for all the help.

---

### Post by linuxopjemac on 2010-05-18
Start reading [here]("http://mac.linux.be/content/apple-powerpc-wiki"). That website has a lot of info.

---

### Post by G33shooter on 2010-05-18
With my specs, I was thinking of installing as follows:

28.72GB OS X     partition 1 HFS+ Journaled
21.69GB Shared  partition 2 non-journaled/non-case sensitive [macOSextended]
20GB      Ubuntu partition 3 (is this called root? "/"?)
4GB        Swap   partition 4  (not sure what type to make this?)

also, what's the deal with ext1, ext2, ext3, ext4 etc.?  Which partitions above do I make ext1,2,3,or4?  Ext is the file type that linux can read, correct?

Not sure if this is correct, I'll do more reading on the link above and googling--if anyone has any other input, that would be great.  Thanks!

---

### Post by linuxopjemac on 2010-05-18
> also, what's the deal with ext1, ext2, ext3, ext4 etc.? Which partitions above do I make ext1,2,3,or4? Ext is the file type that linux can read, correct?

correct. I would take ext4, it's the fastest.

---

### Post by G33shooter on 2010-05-18
Would another easier way to dual boot os x and ubuntu be just running Gparted on the live cd and shrinking the current hard drive and leaving the new space unallocated?  Then run the installer and use the option to 'use the largest continuous free space?'

Wouldn't this allow a simple dual boot or would it screw something up?

---

### Post by linuxopjemac on 2010-05-19
I read that this is possible. I would however ALWAYS make a backup. Within OSX you can use Carbon Copy Cloner. Or maybe nowadays it's easy with Time Machine.

---

### Post by Frobber on 2010-05-19
> **G33shooter said:**
> With my specs, I was thinking of installing as follows:

28.72GB OS X     partition 1 HFS+ Journaled
21.69GB Shared  partition 2 non-journaled/non-case sensitive [macOSextended]
20GB      Ubuntu partition 3 (is this called root? "/"?)
4GB        Swap   partition 4  (not sure what type to make this?)

also, what's the deal with ext1, ext2, ext3, ext4 etc.?  Which partitions above do I make ext1,2,3,or4?  Ext is the file type that linux can read, correct?

Not sure if this is correct, I'll do more reading on the link above and googling--if anyone has any other input, that would be great.  Thanks!


There is a very good description for dual OS installation on a PPC at [http://forums.debian.net](http://forums.debian.net) in the howtos section. Basically he suggests making the first partition linux. I don't recall the reason, I think it is related to the location of yaboot.

On my machine I have linux in the first partition, OSX in second partition, and a HFS partition for user files that can be accessed by both OS.

---

### Post by TheGnomeOfMetal on 2010-05-19
There is not an option to partition in the installer. you must use a partition manager for Macs ( if there is one) to free up unallocated space. though, if you already have unallocated spapce, shown in the installer, then you could use that. OS X could be taking up your entire hard drive, just like windows Xp or vista or 7. if that 46.22 GB space is unallocated, there is more than enough space to install Ubuntu. otherwise use a parition manager in OS X

---

### Post by jdp on 2010-09-26
> **Frobber said:**
> There is a very good description for dual OS installation on a PPC at [http://forums.debian.net](http://forums.debian.net) in the howtos section. Basically he suggests making the first partition linux. I don't recall the reason, I think it is related to the location of yaboot.

On my machine I have linux in the first partition, OSX in second partition, and a HFS partition for user files that can be accessed by both OS.


Certain older Macs, esp. G3 iMacs and B&W G3 towers, need to have the boot partition entirely within the first 8GB of the drive. Also, one of the important tips is to turn off filesystem journalling in OS X first. 

Journalling in OS X - [http://support.apple.com/kb/ht2355](http://support.apple.com/kb/ht2355)
Turning it on and off via GUI or CLI - [http://support.apple.com/kb/TA21053](http://support.apple.com/kb/TA21053)

---

