---
title: "Install help"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by macruadhi on 2007-01-29
When I try running install under UBUNTU 6.06 I select "Use largest continuous free space" and I get the error message " Failed to partition hard disk" I have also tried Suse and it tells me it is unable to resize partition due to inconsistant FS (File system?) 

I am trying to install on a Dell inspiron laptop with a 100gb hdd. It originally had a 21gb windows partition meant for file backup, but I deleted it with Partition Magic. I've run defrag, scandisk with no improvement.

Thanks to all
Eric

---

### Post by ieee488 on 2007-01-29
Can you post a screen capture of what your Partition Magic is showing for your hard drive?

---

### Post by louieb on 2007-01-29
If your comfortable using Partition Magic. Then you should have no trouble using the manual partitioning option of either the live or alternate CD. Either one just select the unused space and create a partition using all the unused space except for a half gig or so. This will be you install / (root) partition so look for format and tell it ext3. After that you will have the half gig left, so create a partition from it and format it as swap. 
Then let the install continue.
I haven't install SUSE but it should have a similar manual partitioning option.

---

### Post by seshomaru samma on 2007-01-29
> **ieee488 said:**
> Can you post a screen capture of what your Partition Magic is showing for your hard drive?

or alternatively ,boot from the Ubuntu live disk , open a terminal and post the output of the command:
```
sudo fdisk -l
```
(-l is letter L not number 1)

---

### Post by jvc26 on 2007-01-29
Have you made sure to defragment your existing partitions at least twice (esp with XP NTFS partitions) as otherwise it cant resize the partitions due to the data being fragmented across the disk.
Il

---

### Post by macruadhi on 2007-01-30
I had already run windows defrag, and I just tried it again. It's not very good. Here's a screenshot of my disk usage before and after another round of defrag

[http://i143.photobucket.com/albums/r125/macruadhi/defragpic-1.jpg](http://i143.photobucket.com/albums/r125/macruadhi/defragpic-1.jpg)

It seems that it will actually be MORE fragmented :(

---

### Post by macruadhi on 2007-01-30
[QUOTE=louieb;2078513]If your comfortable using Partition Magic. Then you should have no trouble using the manual partitioning option of either the live or alternate CD.


Actually, it terrified me to run it. I was sure I'd screw up another HDD trying to install linux. (Yes, I've rendered one of them completely useless.)

---

### Post by mikewhatever on 2007-01-30
Assuming that you have Windows installed, run the CHKDSK check on the partition you've been trying to resize. Then you should be able to repartition. To run CHKDSK on the C partition, open My Computer, right click on C, choose properties, tools, and then the first option, place the check marks into the boxes, and reboot.
I should take a while, depending on the disk size.

I've looked at the screenshot, and thought you might want to defragment a little better. Try installing Deskeeper trial version and defragmenting with it.

---

### Post by Sef on 2007-01-30
Use [Gparted]("http://gparted.sourceforge.net").   Partition Magic and Linux are often not compatible for some reason.

---

