---
title: "Windows/Ubuntu dual-boot"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by oli888 on 2006-11-25
Hi,

I'm trying to dual-boot Windows with Linux, but I'm confused by many of the guides I have tried.

I want to have my partitions like this:

|------WINDOWS------|-----------LINUX-------------|

I'm unsure about whether or not I need to install GRUB, whether it should be on the MBR or on the partition, and which partition should be flagged as "Boot".

---

### Post by bulldog on 2006-11-25
First you have to make room for Ubuntu.
For a try out you need about 10-15GB free space.

If you have just one large c:\ drive you have to defragment windows several times and resize the partition afterwards.

Download the gparted live cd and burn it to a disk,it's only 25-30MB.

[http://sourceforge.net/projects/gparted/](http://sourceforge.net/projects/gparted/)

Boot this live cd and resize your partitions if necessary.
Make a swap of about 1GB and an ext3 partition for your /  [root] partition.
If done exit the gparted live cd and boot into the Ubuntu live cd.

Start the installer and answer the questions.
When you come to the partitioner choose manually,and mount swap as swap and the ext3 as /  [root] and format them.
The rest should be done without a glitch.

You need GRUB to start Ubuntu so you better install it :D 
It will add an entry for your windows to,so you can choose which OS you want to boot.

Good luck.

---

### Post by oli888 on 2006-11-25
Thanks - I'm gonna try it later today :-D

---

### Post by shpook on 2006-11-25
Try to install windows first.

If windows is installed after Ubuntu it will overwrite the boot sector and you'll have to fix that problem manually to be able to boot into Ubuntu again.

If on the other hand you install Ubuntu after windows then, as previous poster mentioned it will automagically add entry for windows and you'll have no problem booting into either OS.

---

