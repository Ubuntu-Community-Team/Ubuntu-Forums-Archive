---
title: "partition questions"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by hellfried on 2006-04-13
i was just wondering how much disk space is considered enough for linux. right now i have allocated 10G of my hd for ubuntu. i have read up on swap partition and am wondering if i need it and how much would i need? i have 1G of RAM and some people say that i might not need a swap at all. there is also the question of where the swap should go. some say at the beginning of the disk, some say at the end. this is all very confusing. 

right now i have a western digital 160G hd. before linux i had 2 partitions of 80G each namely C: (where windows xp is located) and F. i have installed ubuntu on the F: partition. a funny thing though. it did not install where i wanted it to. i wanted linux at the start of F: but when looking at the partitions in partitionmagic, i noticed that there is still a F: partition followed by the linux parition and after that unallocated space. i used partitionmagic to make the unallocated space into parition G.
is it possible for me to shift the linux parition over to F or at least expand it to include F? alternatively should i use F as the swap parition?

i later installed gparted on ubuntu and this is what i get (see attachments). i can't seem to make any changes to the partitions and there are all these exclamation marks beside them. what should i do?

---

### Post by Sef on 2006-04-13
> i later installed gparted on ubuntu and this is what i get (see attachments). i can't seem to make any changes to the partitions and there are all these exclamation marks beside them. what should i do?

To make changes, you can't be using GParted on the hard drive that is mounted.  Instead either download Ubuntu Live CD and use GParted off of it.    Applications > System Tools > GParted

---

### Post by plors on 2006-04-14
usuallly the exclamationmarks mean gparted was unable to read the contents of the filesystem which is in most cases the effect of some missing plugins (in this case ntfsprogs)

Please use the latest [gparted livecd (25MiB)]("http://gparted.sourceforge.net/livecd.php") to be ensured of the latest software.

---

