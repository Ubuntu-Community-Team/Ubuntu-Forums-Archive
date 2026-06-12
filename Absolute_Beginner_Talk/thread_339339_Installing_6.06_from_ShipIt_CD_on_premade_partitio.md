---
title: "Installing 6.06 from ShipIt CD on premade partition"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Inanzu on 2007-01-15
I already have 5 partitions on my HDD. I have one free partition which I would like to install Ubuntu on. I ordered the ShipIt CD's and they came through today and was pretty excited. I plonked the CD in and booted it to the live version and proceeded to install it from there. All is well.

However, I get to stage 5 and I am completely lost. I consider myself to be pretty tech savvy, I am doing a degree in computing etc, so goodness knows how people not familiar would find it.

Basically I want to install it on a partition which is already there, and just "install" it. I dont want to know about how big the swap disc should be, I want the installer to take care of that for me. And what is with the installation needing 3 partitions? One for "/", swap, and /home?

This is the first time I have tried to install Linux, but thought Ubuntu would be the easiest to install, but is prooving pretty tricky :(

Any help would be appreciated.
Thanks.

---

### Post by aysiu on 2007-01-15
You don't need a separate /home partition, but you do need a separate swap one. If you don't already have a swap partition, you'll need to carve one out of your free partition.

Select **Manually Edit Partition Table**. Right-click on the free partition and choose to resize it. Make it about 512 MB smaller (just an example--swap should be roughly 1.5-2 times larger than your RAM). Format the larger free partition as Ext3 and the smaller newer free partition as swap.

Then, when you're going to the next step of the process, uncheck the **Format partition** box next to every partition except the two you just created. Mount the big one at / and the small one as swap. Do not create a separate /home partition. I think the installer will force you to select a mount point for every partition. Just select something random like /media/mount1 or /media/mount2 but be sure *not* to reformat your other partitions.

I've attached a picture of what this looks like.

---

