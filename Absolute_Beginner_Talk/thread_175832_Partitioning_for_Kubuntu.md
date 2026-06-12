---
title: "Partitioning for Kubuntu"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by Israfel on 2006-05-13
I decided to dual boot Kubuntu/Win XP on my laptop but I need to know; how many gigabytes of memory should I put in the windows, kubuntu, liux swap space, and FAT32 partitions if I have a laptop with 37.2 gb of hd memory and 191 mb of RAM?

---

### Post by Sef on 2006-05-13
[QUOTE=Israfel]I decided to dual boot Kubuntu/Win XP on my laptop but I need to know; how many gigabytes of memory should I put in the windows, kubuntu, liux swap space, and FAT32 partitions if I have a laptop with 37.2 gb of hd memory and 191 mb of RAM?[/QUOTE]

XP = 10 GB

Kubuntu = 7 GB

Swap = 400 MB

FAT32 = 5 GB

Home = 10 GB

For info on dual booting, read this excellent tutorial:

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by aysiu on 2006-05-13
I would do this:

15 GB /windows NTFS
6 GB / Ext3
15.8 GB /home Ext3
384 MB swap

Forget the FAT32 partition. You can read/write Ext3 from Windows just fine with [http://www.fs-driver.org/](http://www.fs-driver.org/), and, frankly, you don't have the hard drive space to spare for a FAT32 partition.

I'm suggesting a separate /home partition because beginners especially (but sometimes old-timers, too) find themselves either having to reinstall (because they screwed up their installation) or wanting to reinstall (when a new version of Ubuntu comes out, and they'd rather have a clean installation than upgrade).

A separate /home partition allows you to reinstall without affecting your files and settings/preferences.

Side note: 192 MB of RAM isn't a whole lot. I'd recommend using Xubuntu instead of Ubuntu or Kubuntu:

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

And for setting up a dual-boot, nothing beats this tutorial:
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

---

### Post by Israfel on 2006-05-13
Thanks for the reply but, what is the hame partition for? I haven't seen it mentioned in the guides I was going by.

---

### Post by Israfel on 2006-05-13
Ahh, thanks Aysiu (posted while I was writing my last reply).

---

### Post by Israfel on 2006-05-13
What are the primary differences between the GNOME/KDE desktop environments and XFCE?

---

### Post by aysiu on 2006-05-13
[QUOTE=Israfel]What are the primary differences between the GNOME/KDE desktop environments and XFCE?[/QUOTE] Gnome and KDE:
[http://www.psychocats.net/essays/kdevsgnome](http://www.psychocats.net/essays/kdevsgnome)

XFCE... it's kind of its own thing. It's very fast, but it lacks a few things KDE and Gnome have--move to trash (as opposed to delete) is the one thing that springs to mind, but if you use Nautilus (Gnome's file manager) in XFCE, that takes care of that.

---

