---
title: "Dual Booting and shared partition"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by jd8001 on 2008-03-06
Hey,
         I can't seem to find a straight answer to my question (although I freely admit I haven't looked hard enough). I'm about to set up a dual boot with XP and Ubuntu, and I really want a shard partition that can be read from both os's. If I start in windows, do I simply defrag the Hard Drive, then create a small (5 gig ) FAT32 partition on that Hard Drive, then when I'm installing Ubuntu is there some way I can tell it to only resize one partition (i.e. the big one) and leave the other one alone. Then I can mount the shared partition and read its files, correct? Also, is there anyway way to load XP onto a machine with just UBUNTU, or am I going to have to load Ubuntu onto a machine with just XP? 


JD

---

### Post by Kiri on 2008-03-06
You can just do all that partitioning stuff in the ubuntu install I believe. Just prep the partition by defragging and make sure you have enough free space. 
Then make the Ubuntu partition and the share partition when you install Ubuntu.

I think its possible to do both, but installing XP first, then ubuntu is apparently much easier

---

### Post by herbster on 2008-03-06
Yeah, you can do that in the install using the Manual option when you arrive at disk options. As Kiri said just defrag the drive in XP first.

XP first then Ubuntu is easier, but if you have installed Ubuntu first then install XP, you simply have to use a Live CD to reinstall GRUB. It's not difficult, just more convenient the other way.

---

