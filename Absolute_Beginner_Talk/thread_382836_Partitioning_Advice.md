---
title: "Partitioning Advice"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Mr. Smiley on 2007-03-12
I need some partitioning advice. I have Vista installed on the third partition of my e1505 laptop. I don't want to touch that partition. Dell comes with 3 other partitions pre-installed. One of 10.7GB which holds backups which I don't need, one 2.1 GB for MediaDirect which I uninstalled because it had a memory leak so I don't need it, and one 49.3 MB partition that I can find no information on. So I want to format the 10.7 GB and 2.1 GB partitions to make room for an Ubuntu server install. I need advice on how to reformat these partitions. I tried the one build into the ubuntu server install but I can't figure out how to merge the 2 partitions into one big free space to set up the partitions. 
Any help would be appreciated.
Also, does anyone know what the 49.3 MB partition is for? It's the first partition and it is a fat16 primary partition.
Thanks!

---

### Post by az on 2007-03-12
> **Mr. Smiley said:**
> I need advice on how to reformat these partitions. I tried the one build into the ubuntu server install but I can't figure out how to merge the 2 partitions into one big free space to set up the partitions. 


You delete them.  Then they become one large FREE SPACE, listed in the list of partitions after that.

---

### Post by OffHand on 2007-03-12
nvm

---

### Post by Mr. Smiley on 2007-03-12
I tired that but the two partitions that I want to delete are in between the windows partition and I can't figure out how to "merge" the two free spaces together.
Picture of what I am talking about:
[Pic]("http://img.photobucket.com/albums/v630/MistaSmiley/Partition.jpg")
Btw, thanks for the fast replies!
Also, is 4 the maximum amount of partitions allowed on a disk?

---

### Post by OffHand on 2007-03-12
> **Mr. Smiley said:**
> I tired that but the two partitions that I want to delete are in between the windows partition and I can't figure out how to "merge" the two free spaces together.
Picture of what I am talking about:
[Pic]("http://img.photobucket.com/albums/v630/MistaSmiley/Partition.jpg")
Btw, thanks for the fast replies!

Not possible if they ain't next to each other.

---

### Post by Mr. Smiley on 2007-03-12
Well, I will reinstall vista if I must but could I delete both partitions, resize the third partition to include the free space, then resize the third partition to get the free space at the back of the drive? What this be a pretty risky operation?

---

### Post by OffHand on 2007-03-12
> **Mr. Smiley said:**
> Well, I will reinstall vista if I must but could I delete both partitions, resize the third partition to include the free space, then resize the third partition to get the free space at the back of the drive? What this be a pretty risky operation?

I don't think you are able to do this. Please someone confirm this.

---

### Post by Mr. Smiley on 2007-03-12
Ok, I just found a link how to shrink/expand partitions in Vista. [Here]("http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/"). If it doesn't work I will just reformat. Thanks for your help!

---

### Post by OffHand on 2007-03-12
> **Mr. Smiley said:**
> Ok, I just found a link how to shrink/expand partitions in Vista. [Here]("http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/"). If it doesn't work I will just reformat. Thanks for your help!

If you need to re-install, install Vista first. Ubuntu will recognize Vista but Vista will not recognize Ubuntu.

---

