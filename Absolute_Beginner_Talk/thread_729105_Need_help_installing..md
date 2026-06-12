---
title: "Need help installing."
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by necronzero on 2008-03-19
Ok, so I wanted to install Ubuntu on my PC BUT i want to keep my windows partition. Is there a way to allot 20-30GB for Ubuntu???
Thanks in advance.

---

### Post by philinux on 2008-03-19
Read thoroughly and plan. Loads of info here.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by billgoldberg on 2008-03-19
I presume you just have 1 big partition for windows.

In windows defrag the hard drive.

Pop in the ubuntu cd, use guided (with the slider).

That should work (unless I'm very wrong).

I always first partition the hard drive using the [gparted live cd]("http://gparted-livecd.tuxfamily.org/").

Then you can install gusty on the second partition.

---

### Post by necronzero on 2008-03-19
Thanks. Ill try this out

---

### Post by bren on 2008-03-19
yes, the standard Ubuntu 7.10 live CD will do this for you

here are a few corner cases i have heard about
some of these may be old news or out of date now

1) if your current OS is VISTA, some report difficultites for the Ubuntu installer to resize the original VISTA partition.    if this happens then use VISTA parition editior (part of standard vista to free up the space first.    Then install ubuntu in the free space
2) if your current OS is XP run defrag at least twice before you begin Ubuntu install
3) if you have a low spec computer (<256MB ram) then use the "alternate" CD to install

For much more on dual boot see

1) [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
2) [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

who are well respected third party installation guides

---

### Post by bumanie on 2008-03-19
Do as above re setting up the partition/s, but also it is advisable to make a separate /home partition in addition to the mandatory / and swap. To do this you need to use manual partitioning. The advantage of a separate /home is that if somehting corrupts your file system, you can install ubuntu to / and the files in /home will be safe (that's how I do it).

---

### Post by necronzero on 2008-03-20
Ok, i reinstalled Vista and created 2 partitions, 1 for Windows and 1 for Linux (85GB and 25GB) When i access the installation process it always chooses the windows partition and not the free one, and i dont know how to set it up manually, can someone help me???

---

### Post by jan quark on 2008-03-20
also a nice dual booting site:

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

