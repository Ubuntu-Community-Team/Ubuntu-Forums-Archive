---
title: "Does Swap Count As A Real Partition?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by OffHand on 2008-04-17
Hi

I ordered a new laptop which has 4 partitions installed. 

1. A small Dell utility partition (about 110 MB). Needed for testing so best is not to remove it. 

2. Media Direct partition. Don't need it. Gonna be deleted.

3. The partition with Windows Vista. Unfortunately I need this for gaming and work.

4. 10 GB grote recovery partition. Gonna be deleted. I'll use the dvd's.

Now if I give /home it's own partion and I need a swap I need 5 partions. 

My question is if swap counts towards the limit of 4 (primary) partitions. 

Thanks in advance.

---

### Post by Moop on 2008-04-17
If swap is created as a primary partition it counts. Create one large extended partition and put all your other partitions in it. They will all work fine as logical partitions which don't count.

---

### Post by Oldsoldier2003 on 2008-04-17
> **Moop said:**
> If swap is created as a primary partition it counts. Create one large extended partition and put all your other partitions in it. They will all work fine as logical partitions which don't count.

yep swap is usually housed on an logical partition. no reason to put it on a primary partition... in fact Ubuntu will put it on a logical partition when it creates it...

---

### Post by SunnyRabbiera on 2008-04-17
Yes it does, however you can install ubuntu without a swap partition.
But if you dont have a lot of memory you may need it, heck even i still use swap with my 1gb of memory as a just in case measure.
but swap really isnt usually that big, mine is set at 878 MB

---

### Post by OffHand on 2008-04-17
> **Moop said:**
> If swap is created as a primary partition it counts. Create one large extended partition and put all your other partitions in it. They will all work fine as logical partitions which don't count.
> **Oldsoldier2003 said:**
> yep swap is usually housed on an logical partition. no reason to put it on a primary partition... in fact Ubuntu will put it on a logical partition when it creates it...

So you are saying that I should be able to create a swap even if I keep the utilities and vista partition I can create a /, /home and swap by keeping the defaults?

---

### Post by notwen on 2008-04-17
> **OffHand said:**
> So you are saying that I should be able to create a swap even if I keep the utilities and vista partition I can create a /, /home and swap by keeping the defaults?

Combine your whole Linux install into a extended partition.  This will make a partition in which you can split up into more logical partitions.  You can use Gparted or any partition software you're comfortable w/ using.  As always you may want to backup any needed data before changing your HDD's partitions.  Post back if you need further explanation.  [Here]("http://www.linfo.org/extended_partition.html") is a brief explanation of what a extended partition is.

---

### Post by The Cog on 2008-04-17
You can't use the default installer settings for that. I read that you want to remove partitions 2 and 4. You want to add 3 partitions, root, home and swap. You will need an extended partition to put the logical partitions into. You don't give the partition sizes, but I reckon you need around 5G for root. With luck one of the gaps will be around that size. Then you can put home and swap in the other gap in an extended partition. I am not at all sure it's a good idea to move the Vista partition around.

It's probably best to use the partition editor in the live CD to delete the old partitions and create the new ones, then use the installer and manually tell it how to use the partitions.

---

### Post by bumanie on 2008-04-17
Swap or any linux/ubuntu partition is equally as happy in a primary partition or in an extended logical partition. As far as I know, the number of logical partitions you can create is unlimited - at least in theory - hard drive space available will obviously cause some limitation.

---

### Post by Oldsoldier2003 on 2008-04-17
> **bumanie said:**
> **Swap or any linux/ubuntu partition is equally as happy in a primary partition or in an extended logical partition**. As far as I know, the number of logical partitions you can create is unlimited - at least in theory - hard drive space available will obviously cause some limitation.

yup, with the part I bolded in mind, it just doesn't make sense to make swap in a primary partion since they are limited to four...

---

### Post by Thelasko on 2008-04-17
Good thread, I often wondered about this myself.

---

### Post by OffHand on 2008-04-17
Thanks for all the replies guys! I think I should be fine :)

---

### Post by bodhi.zazen on 2008-04-17
See this thread for an overview of partitioning.

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

