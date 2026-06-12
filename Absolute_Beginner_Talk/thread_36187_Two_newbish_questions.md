---
title: "Two newbish questions"
date: 2005-05-22
forum: Absolute Beginner Talk
---

### Post by Fozer on 2005-05-22
Yeah, the title is pretty self-explanatory, so I'll just skip straight to the point:

Question 1: Whenever I boot from the live cd, it goes through all the normal boot processes, but before it gets to the configuration(choosing languages, etc.), it resets and boots Windows. However, I've tried it on another computer and it works perfectly fine. I know I set up the BIOS right because it does boot, but it resets and boots from the hd. Anyone know what might be causeing this and how to fix it?

Questoin 2: I know this has probably been asked millions of times before, but I've read at least 3 or 4 tutorials on this subject, and am still rather clueless as to one thing. That "thing" is how to partition my hd to make it dual-boot without losing any data. From what I've read, it's possible, but I have no idea how.

Thanks in advance,
                           Fozer

---

### Post by hiptrop on 2005-05-22
1)

just little thought ... did you save the bios settings ?

2)

if you have never done it before i suggest you use a product like arcronis partition expert or partition magic ! 

just do a linux partition in windows and a swap file ! 

then install linux on that NEW partition and linux will configure grub itself !

other way : make a start disc ( floppy ) and type fdisk ... then you can do it manually in dos !

but if you don know what you are doing you should use a product i mentioned ( or something similar  ! )

---

### Post by mtron on 2005-05-22
The easiest way is just to resize your Windows HD with partition magic (or with a freeware tool like [http://www.sysresccd.org/](http://www.sysresccd.org/)  always good to have  ;-) ) and make around 10 GB of free space, then boot the hoary install cd, and the partitioner pops up.

Choose: manually edit partition tabe, navigate to the line, where it says "free space" and click enter, then "setup partion automatically" and you are done.

Really very easy!

---

### Post by JimmyBEng on 2005-05-24
As for your second question the Hoary installer can shrink a NTFS partition.  It is risky business though.  I did it myself though with no problems.

First before you install, backup anything critical (of course) and defrag the drive, this should compact the files to the front of the partion (hopefully).   When you reach the partition step of your install, say that you want to manually edit the partition table.  Select the NTFS partiton, and say you want to modify it.  then change the size, I recommend you have your math done ahead of time.   Then you can create any other partiotions, etc.

Just be careful, selecting the wrong option will destroy your windows installation.  But if you are confident and careful, you should be able to do it, no prob.  And without having to buy partition magic.

---

### Post by az on 2005-05-24
Resizing NTFS partitions is quite safe.  That is no excuse to not make a backup of your data, though.

Many many people have done it with the Ubuntu installer (and debian installler) without any problems.

Simply use manual partitioning.  Select your windows partition and give it a smaller size.  If the installer cannot do something, you do not get presented with the option on the screen.  So if it offers you the size of the partition, it should be safe to resize it.

It will ask you if you are sure.  Once you do it, you are shown the partition table with some free space.  Pick guided partitioning and the installer will take care of everyting else from that point on....

As for the live cd, try changing some settings in your bios, or look at the cheatcodes available to you in the F3 F4 F5 F6 and so on screens.

---

### Post by JimmyBEng on 2005-05-24
didn't mean to make it sound as if the resize was unsafe.  when i said risky, I only meant that you have to be careful in making your selections that you don't inadvertantly do damage to the data. Like i said it worked on my box without a problem.

---

### Post by Fozer on 2005-05-26
So all I have to do is make sure that there's enough space at the end of the   windows partition and the install cd can split the partition itself? Sounds easy enough...

And for the live cd thing, I'll just keep messing with my bios until something happens.

---

