---
title: "Partitioning, help ASAP if possible"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Pobega on 2007-01-08
Well I'm trying to partition a /home drive, but the guide on Psychocats.net assumes you have knowledge of partitioning (Which is surprising, only HowTo on that site that does that!)

So I'm using: [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

And I'm stuck on:

[http://psychocats.net/ubuntu/images/home06.png](http://psychocats.net/ubuntu/images/home06.png)

I can't create my new partition as logical

> Now, in my example, my original partition that I shrunk was /dev/hda5, and it created a new partition called /dev/hda7, and my /home folder lives on /dev/hda1.

I only have one normal partition as of right now, and that's /dev/sda1. I'm not exactly sure where my home folder lives, so I find this portion kind of confusing.

---

### Post by harmeet on 2007-01-08
Are you repartitioning your linux harddrive or your windows harddrive?

---

### Post by Pobega on 2007-01-08
Linux, all I have installed is Linux. And I'm repartitioning to make a /home partition, because having to back up my music whenever I want to reinstall Linux is a horrible thing.

---

### Post by harmeet on 2007-01-08
ok then you need to shrink the main partition to a smaller size first. For that you need some contiguous free space at the end of the disk. If you are using gparted tool,  you can use mouse to select the end of the partition and drag it to the left to create space. Then you create a new partition in that free space. It will create /dev/sda2 for you where you can mount your /home later.

---

### Post by Pobega on 2007-01-08
> The following operation could not be applied to disk:

Resize /dev/sda1 from 71.66 GiB to 39.06 GiB

See the details for more information

I have no idea why it didn't work, it didn't even get past "check filesystem on /dev/sda1 for errors"

---

### Post by harmeet on 2007-01-08
Maybe you have data all over the hard disk. Defragment it to bring everything to the begining. Then, you will have some space at the end to shrink the partition.

---

### Post by Pobega on 2007-01-08
How do I defragment the disk?

---

### Post by glabouni on 2007-01-08
not sure you can resize a mounted / partition.

you should try to resize your partition from a live cd, either ubuntu's cd or [sysrescue cd]("http://www.sysresccd.org/")

strangely enough the part were you are stuck is also missing from this tutorial:
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by Pobega on 2007-01-08
That's what I've been doing, I'm not **that** computer dumb. But it's still giving me that error, from a LiveCD.

---

### Post by smoker on 2007-01-08
>  The following operation could not be applied to disk:

Resize /dev/sda1 from 71.66 GiB to 39.06 GiB

See the details for more information


did you click the details box for more information? how much data is on the hard drive, remember you need to allow extra space for manouvring data, for example, if you have 'x' amount of data, resize your partition to 'x' amount+10-15%

---

### Post by Pobega on 2007-01-08
7.10 GB used, I was downsizing from 72 GB to 39 GB. Shouldn't have been anything wrong there.

---

### Post by smoker on 2007-01-08
there should be no problem then, though i have had trouble with the ubuntu gparted before, if you can download the gparted iso from sourceforge.net and make a boot version, i've never had any problems with that.

also, did you click the box for more information?

---

### Post by Pobega on 2007-01-09
> **smoker said:**
> there should be no problem then, though i have had trouble with the ubuntu gparted before, if you can download the gparted iso from sourceforge.net and make a boot version, i've never had any problems with that.

also, did you click the box for more information?
I'll try the gparted ISO, and no, I didn't click the box for more information. All I read was that it couldn't even check for errors, and I knew something was wrong.

---

### Post by Pobega on 2007-01-09
Okay well, I booted from the Ubuntu LiveCD again and this time it seemed to work. Now I have a question: How do I check to see if my /home partition is working right?

**Edit:** Is this evidence sufficient enough? When I'm in / the window says: Free Space: 31.2 GB. And when I'm in /home, it says: Free Space: 26.8 GB

---

