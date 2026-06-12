---
title: "Hard disk upgrade - GRUB gone"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2008-02-22
Hi, I've just had a new 500gb disk put in the main boot slot of my computer and I've run the Parted Magic Linux based disk and used the dd commands to copy my partitions across to the new disk. I managed to successfully migrate all the partitions, however I no longer get the GRUB option to boot Ubuntu. It just boots straight into Windows. The Ubuntu partition has been successfully migrated, I just can't boot it. How can I put GRUB back on without damaging any of the new partitions?:confused:

---

### Post by Presto123 on 2008-02-22
The easiest way is to get SuperGrub (It's good to have anyway). When you boot into the menu of that disk, you can navigate to the Linux MBR (Master Boot Record) and restore it. Someone else will probably have some extra info here if I have missed anything (Which i'm pretty sure I did).

---

### Post by teryowen on 2008-02-22
try bootin up into a live cd and in terminal:

sudo grub
root (hdX,Y)
setup (hdX)
quit

where X is the hard drive for your ubuntu so if its the 1st hard drive would be 0 if its the 2nd hard drive would be 1,
where Y is the partitions for your ubuntu so if its the 1st partitions y would be 0 if the 2nd then y would be 1 and so on change the value accordingly.

---

### Post by Wake Rider on 2008-02-23
> **teryowen said:**
> try bootin up into a live cd and in terminal:

sudo grub
root (hdX,Y)
setup (hdX)
quit

where X is the hard drive for your ubuntu so if its the 1st hard drive would be 0 if its the 2nd hard drive would be 1,
where Y is the partitions for your ubuntu so if its the 1st partitions y would be 0 if the 2nd then y would be 1 and so on change the value accordingly.

I am using the parted magic Live CD, and I can get into grub, however when I type root (sd0,1) It comes up with the error: Error 23: Error while parsing number.

My main drive is sata so is sda not hda and Ubuntu is on mount point /dev/sda2. What is the command I need to type?:confused:

---

### Post by Wake Rider on 2008-02-23
I tried typing root (hd0,1) 
This time it came up with: Filesystem type unknown, partition type 0x82

---

### Post by Wake Rider on 2008-02-23
Never mind, I found the answer in another thread. Thanks Glennric! Here is the link to that thread:

[http://ubuntuforums.org/showthread.php?t=705321](http://ubuntuforums.org/showthread.php?t=705321)

---

### Post by logos34 on 2008-02-23
[just solved]

---

