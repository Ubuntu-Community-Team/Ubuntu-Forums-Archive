---
title: "ubuntus partition share"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by skiddly on 2007-02-26
Have looked in forums couldnt find exactly what im after unless i missed it . i have 80gig hd partitioned 40 xp 40 ubuntu now im getting a little easier on ubuntu i want to assign more to it 20 xp and 60 ubuntu how do i do it if its complicated i leave it alone also can you partition an external hard drive and how thanks in advance:guitar: linux rocks

---

### Post by bodhi.zazen on 2007-02-26
Very, very easy ...

I would use the gparted live CD :

Gparted:

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Download: [Download Gparted](http://sourceforge.net/project/downloading.php?groupname=gparted&filename=gparted-livecd-0.3.3-7.iso&use_mirror=osdn)

---

### Post by DigitalRanger on 2007-02-26
> **bodhi.zazen said:**
> Very, very easy ...

I would use the gparted live CD :

Gparted:

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Download: [Download Gparted](http://sourceforge.net/project/downloading.php?groupname=gparted&filename=gparted-livecd-0.3.3-7.iso&use_mirror=osdn)

Hi there (my first post here),
I'm a Windows user who is making the switch ...

*(Have long wanted to learn linux but never had time - but the evils of Microsoft finally gave me the push).*

... In Windows I'm used to manipulating partitions with "Partition Magic". With this application, I can non-destructively move a partition up or down a down a disc. From what I've seen of Gparted, it looks like you cannot move a partition (or more precisely, you can't change the start position).

Am I correct in this, or can GParted actually shift a whole partition of data up or down a disc without destroying the data contained therein?

Thanks.

---

### Post by bodhi.zazen on 2007-02-26
The gparted disk can do it all.

Note: gparted is on the Ubuntu desktop, but the gparted live CD has a newer version and IMO well worth the download.

Note2: Partition magic does not always play well with Linux partitions. You should probably change over to something like gparted.

Note3: gparted can handle FAT and ntfs partitions no problem :)

---

### Post by DigitalRanger on 2007-02-26
Thank you  - I must admit I've paid little attention to the GParted on the liveCD. I just looked at what was installed on the Ubuntu desktop.

I'm currently 'playing' with virtualised Ubuntu (using VirtualBox).

---

