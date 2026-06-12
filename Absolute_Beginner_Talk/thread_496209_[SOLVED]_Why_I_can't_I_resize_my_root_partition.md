---
title: "[SOLVED] Why I can't I resize my root partition?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-07-08
I've allocated free space adjacent to my root partition and booted off the Live CD.  However I still can't resize the partition using gparted.  When I try to resize it lists 0MB free before my root partition.  What gives?

---

### Post by bren on 2007-07-08
the little padlocks show that these partitions are still mounted

you can resize them after you unmount them or you can boot from a gparted live cd ....

type "man umount" for more info

hope that helps

bren

---

### Post by AncientPC on 2007-07-08
The partitions in question are unmounted and do not have padlocks on them.

---

### Post by overdrank on 2007-07-08
> **AncientPC said:**
> The partitions in question are unmounted and do not have padlocks on them.

Hi I believe it is be cause you already have 4 partition on the drive and that is the limit. I you want to you will have to delete one or more partitions and then make a extended partition then you will be able to make more partitions. Hope this helps!:popcorn:
Edit. I see you have a extended partition and that is where the additional partition well have to be made.

---

### Post by AncientPC on 2007-07-08
I only have 2 primary partitions and one logical partition.

---

### Post by AncientPC on 2007-07-08
It worked with the GParted LiveCD.

---

### Post by taisao on 2007-07-09
I also want to allocate some free space from my ntfs partitions for the ubuntu partition. When you resize the ntfs partition, did you do it in windows or in ubuntu?

---

### Post by AncientPC on 2007-07-09
I did it in Windows with Partition Pro, but it required a reboot.

You can use the GParted LiveCD to do the same thing.

---

### Post by taisao on 2007-07-09
my newly created unallocated space is to far away from the root partition :(

oh well, 1.3 gb free is still okay

---

### Post by AncientPC on 2007-07-09
You should be able to move it over adjacent to your linux partition.

I freed up space and moved it out of my logical partition and next to my linux partition before merging it.

Also, the Gparted LiveCD is much better than the Ubuntu LiveCD's Gparted.

---

