---
title: "[SOLVED] Re-Installed Ubuntu Won't Boot"
date: 2008-06-19
forum: Apple Hardware Users
---

### Post by ninjapenguin on 2008-06-19
My ndiswrapper got messed up and created an infinite loop, which starts up whenever you boot up Ubuntu.  So I had to re-install Ubuntu. So I reformatted the partition to erase all of the data on it and it installed smoothly, but when I tried to boot it up, I get the grey Tux freeze from rEFIt.  So I booted into my live cd of Ubuntu, and installed grub on the partition with Ubuntu on it, but it didn't fix the problem. :confused: Do I just have to delete my partition and re-create it?

---

### Post by cyberdork33 on 2008-06-19
Does OS X work? can you post the information reported by the partition tool in your Utilities folder?

---

### Post by ninjapenguin on 2008-06-19
OS X works fine, and I still haven't tried XP yet because it was late when this happened, but as soon as I get home I'll try XP and get the read out of the partitioning tool, but when I tried it when I got the the rEFIt screen it said everything was in sync.

---

### Post by cyberdork33 on 2008-06-19
> **ninjapenguin said:**
> OS X works fine, and I still haven't tried XP yet because it was late when this happened, but as soon as I get home I'll try XP and get the read out of the partitioning tool, but when I tried it when I got the the rEFIt screen it said everything was in sync.
Even if they are in sync, there are other things that might cause the problem related to partitions.

Since you also have XP on your Mac, you might have broken the Windows bootloader. This can be fixed by booting the Windows CD into recovery mode and using the FIXMBR command.

---

### Post by ninjapenguin on 2008-06-19
Okay I got home and tried ubuntu and now it works and I have no clue what changed from last night and today, but thank you for helping.

---

