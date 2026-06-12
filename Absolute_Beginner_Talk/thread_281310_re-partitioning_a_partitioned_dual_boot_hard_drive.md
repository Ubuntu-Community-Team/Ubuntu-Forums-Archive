---
title: "re-partitioning a partitioned dual boot hard drive"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2006-10-20
I have a dual boot XP and Dapper - going great!

I have deleted lots of crap on XP and find that I now want to increase the dapper partition and reduce the XP partition. Can I do this? If so how? I am in Dapper now and have just defragmented my ntfs partition where XP resides.

Any assistance is appreciated.

:-D

Tchoklat

---

### Post by catlett on 2006-10-20
Use gparted live.[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) It is the same gparted that is installed on ubuntu but it runs from a cd. Download the iso, burn it to a disk and then boot to it. You need to do it this way because you can't change a partition that is mounted and obviously ubuntu's partition will be mounted if you're running ubuntu off of it.
There are limitations to where you can add space. I think it is something like you can only add to the right of a partition. Regardless, gparted won't attempt any operation that isn't possible so you will know right away if it is do-able.
First resize your XP partition by selecting it and choosing "resize". Then you will select the ubuntu drive and select "resize". That is when you will find out if you can add that space to ubuntu. If you can't add it to ubuntu's partition, you can make it an ext3 linux filesystem and mount it as a data partition for ubuntu. That way you get to use the space. Aysiu's guide to mounting a linux partition will explain how to add a linux partition to your ubuntu system [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by FastZ on 2006-11-07
Paragon Partition Manager for Windows will allow you to grow a partiton to the LEFT if you need to.  That's what I did but now the added space I incorporated into my ext3 partition isnt showing up as being used.  I've read that you have to "resize the file system" or something like that but just like everything else in Linux (AFAIK) finding a thorough how-to for performing this is next to impossible.  Any help?

---

