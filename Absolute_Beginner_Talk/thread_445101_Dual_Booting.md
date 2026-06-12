---
title: "Dual Booting"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by sperrett on 2007-05-15
I had a look at other threads but didn't see (or understand) any post which related specifically to my problem.

I'm absolutely new to Linux (still counting in hours).  I ran the live CD and like it so wanted to go the next step and install it on the hard drive.  I see that if I double click the install icon it will do everything for me and partition my current windows drive and so on.

My problem is that my current windows drive is 60Gb and almost full.  Can I install Ubuntu on a physcally separt drive to windows and still have it dual boot?  I have 2 other hard drives to my computer.

Ideally i would like to partition one of the other drive which have lots more room.  Believe it or not but I have moved as much off the windows drive as i can and it still can only get 8 GB free.  I don't want to use this space because as I continue to use windows it will want to use some of this space.

Thanks

---

### Post by oilchangeguy on 2007-05-15
read this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by loserboy on 2007-05-15
I didn't read the link, but just to answer your question, yes, thats how i have it, all I did was tell it to make the entire drive a logical drive then set my partitions the way i want inside the logical partition

eta: grub the bootloader still knows where to install itself on the boot sector of your primary hard drive so it's not an issue

---

### Post by sperrett on 2007-05-15
I had read that link but it didn't totally clear things up for me.

The way I read it is that there is 3 options.  Option 2 is to do away with windows altogether, which is not what I want.

Option 1 will shrink my windows partition.  I didn't want to do this because I still need to use this space for windows functions.

So I will do option 3.  The problem I had with option 3 is that it didn't seem clear.  Should I see my 3 drives listed here and just pick one with some free space?  I assume that "use as" should be ext3 and what should mount point be?

---

### Post by oilchangeguy on 2007-05-15
i dual boot with 2 hard drives, a fresh install of ubuntu 6.06 on a 30gb hd. and a fresh install of windows xp pro (legal copy) on a 10gb hd. (small drive, windows is there, just in case) had no problems. do you have anything stored on both of your other drives?

---

### Post by crimesaucer on 2007-05-15
I found this site explains a lot about different installing methods:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Plus it has easy to follow directions with pictures.

The guide also mentions these links for your situation: 

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

and:

[http://ubuntuforums.org/showthread.php?t=120994](http://ubuntuforums.org/showthread.php?t=120994)

---

### Post by sperrett on 2007-05-15
oilchangeguy,
There is data on the other drives but no other operating systems.  Correct me if I'm wrong, but I can add a partition to a drive with space without losing the data already on the drive.

My biggest problem is that I rely heavily on my windows based desktop (for now) and don't have another computer to play on.

---

### Post by oilchangeguy on 2007-05-15
> **sperrett said:**
> oilchangeguy,
There is data on the other drives but no other operating systems.  Correct me if I'm wrong, but I can add a partition to a drive with space without losing the data already on the drive.

My biggest problem is that I rely heavily on my windows based desktop (for now) and don't have another computer to play on.

yes you can add another partition, just use gparted from the live cd to resize.

---

### Post by jerrylamos on 2007-05-15
Resize works best if the data on the existing partition has been shoved to the front, in the case of XP try defrag.  Then resize the end of the partition back toward the front, having made sure there is no data in that part of the partition.  Do you have any way to make sure the data on the other drives is toward the front of the partitions?  

BTW, good choices are something like 20 gb for the root /  partition and 512mb for a swap partition, unless you plan on storing a lot of photos or music.

Cheers, Jerry

---

### Post by xthund3rh3adx on 2007-05-15
Doesnt have to be big, i have ubuntu on a mere 7GB one. It will run fine.

---

