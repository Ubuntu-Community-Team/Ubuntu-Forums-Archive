---
title: "Problems booting"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Aberrix on 2006-10-05
Alright, I've been getting set up all week and I've run into a show stopper. Please help.

I have 3 hard drives, according to my BIOS they are as follows;
SATA Master 1: 74GB Raptor (Windows XP - NTFS)
SATA Master 2: 74GB Raptor (Ubuntu - Ext3)
SATA Master 3: 250GB Segate (Storage - Etx3)

First I disconnected my storage drive because it was making things weird during the first trial of install(s). Because I was comming from a RAID 0 windows setup I first deleted the array and then installed a fresh copy of XP on my first drive and once that was up I installed a fresh copy of Ubuntu on the second from the LiveCD. Everything worked like a charm and I was happily plugging away at getting things to work.

Now, I've formatted my storage drive to Ext3 so that I can access it on both OS's and for the future of hopefully kicking the windows habbit ;) I installed the drive and got it working in windows thanks to the fs-driver. One thing I'll comment is that in Partition Magic 8.0 it lists my 250gb drive first, then my windows then my linux drive... Also in Gpartition manager (name?) It lists my 250GB drive first, as sbd1

So I try to boot into Ubuntu from the Grub and I get the following message after booting the kernel;

```
mount: mounting /dev/sbd1 on /root failed no such device
mount: mounting /root/dev on /dev.
mount: mounting /sys (shortened) failed
mount: mounting /sys (shortened) failed
mount: mounting /proc (shortened) failed
target file system doesnt have /sbin/init
```

I shortened up the message but I think you get the point. I am thinking it doesnt know that my linux drive is now sbd3 or sbd2 because I've added the third drive. Which makes me ask the question, why would it think that my third drive on the 3rd sata controller is sbd1 or disk 1 in windows? I think if I just reinstalled it would probably work, but I wan't to figure this out, I wan't to know why it did this and how to fix/correct it. Thanks in advance for your replies.

---

### Post by robinl on 2006-10-05
Maybe you can boot up to a Live CD, use gparted/qtparted to see you new drives' order and change grub? Good thing on Edgy is that fstab now uses UUID so it doesn't matter what name the drive have it will still find it.

---

### Post by Aberrix on 2006-10-06
> **robinl said:**
> Maybe you can boot up to a Live CD, use gparted/qtparted to see you new drives' order and change grub?

how do I change/view the order in grub?

---

