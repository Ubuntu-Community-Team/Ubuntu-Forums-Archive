---
title: "Partition question"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by badgerboyx on 2007-11-26
Hi there, installed ubuntu a few weeks ago. I'm wanting to make a second partition now with gparted to store my music and movies on etc. At present I have one 30gb ext3 partition with the system on it and then a 2 gig swap. I have left 100gb of allocated. In gparted when I click on the free space and new partition I'm not sure if I need to select create primary partition or extended? Also there is free space preceding and free space following values that can be changed. Do I need to touch either of those?

Thanks!

---

### Post by laidback on 2007-11-26
Sometimes you can get a little free space that has remaind unused due to rounding in partition size allocation. If you're able it's helpful to paste the Gparted screen of your hdd so we can see the detail.

---

### Post by ajgreeny on 2007-11-26
If Ubuntu is your only operating system and you don't have files you need on the allocated space (did you mean unallocated?), it may be easiest to delete all the unwanted partitions and start again with gparted by making one or more partitions, getting rid of the free space at the same time.

Disks can only have 4 primary partitions each, but you can use logical partitions to contain as many as you want, so the choice is open to you at the moment if you start with just the Ubuntu system partition and swap, though if you look you will see that swap, usually hda5, is in a logical partition, usually hda2.

---

### Post by indytim on 2007-11-26
My recommendation is to use GParted (or GParted Live) and create 1 extended partition from the unallocated space.  Once that partition has been created, then within the extended partition, create an ext3 partition equal to about half of the extended partition.  For now leave the rest of the extended partition open.  Modify your fstab to auto mount your new partition within your Linux ops.

When you either get crunched for space in the new partition or need to add another new partition, do adjustments within the unallocated space in the extended partition.

IndyTim

---

