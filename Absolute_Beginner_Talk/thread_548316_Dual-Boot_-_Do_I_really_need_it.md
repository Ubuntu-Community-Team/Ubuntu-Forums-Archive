---
title: "Dual-Boot - Do I really need it?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by niceguy123 on 2007-09-11
1. What happens when I just install Ubuntu on a PC that has XP, am I actually formating the disk and losing what I had or is that saved and accessible? 

2. Why would I need a dual  boot? Doesn't XP take up a lot of room on my hard drive?

---

### Post by kane77 on 2007-09-11
> **niceguy123 said:**
> 1. What happens when I just install Ubuntu on a PC that has XP, am I actually formating the disk and losing what I had or is that saved and accessible? 

2. Why would I need a dual  boot? Doesn't XP take up a lot of room on my hard drive?

1. it depends on what you want to do... I guess that by default ubuntu installs (and thus formats it) on the windows partition unless you have some linux partitions..

2. if you don't want to use windows (or any other OS you might have) you don't need dual boot, however to boot into windows you want the dual boot.. (although on my desktop I have two disks and windows is on one, ubuntu is on the other and i only switch drive preference to boot windows or linux...)

---

### Post by mattmole on 2007-09-11
Hi,

I would advise dual booting, especially because you don't know if Ubuntu will do everything you want it to!

XP does not use too much disk space really. It is your movies, sound tracks, work etc that use more. What size HDD have you got?

I cant imagine you needing anymore than approximately 5-7GB for Ubuntu.

Personally, when installing Ubuntu I would first backup all work from your Windows partition, then defragment the drive.

When you reboot with the live disk, Ubuntu will give you the option to shrink your windows partition. You can then create a swap partition (double your RAM maybe, Im never too sure of the size of SWAP), ext3 partition for ubuntu and then a separate partition for your home directory.

The reason for this is so that if you reinstall ubuntu you will be able to keep your home directory as it is.

I hope that helps. I still have a windows dual boot even though I have used Ubuntu exclusively for 2 years.

mattmole

---

