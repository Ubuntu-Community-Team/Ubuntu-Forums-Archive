---
title: "Pre-System overhall help request"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by divorcetheworld on 2007-05-08
I'm not new to computers by any means, but I am new to Linux.  And the questions I have pertain more to the preparation for a dual boot system with two fresh installs, one each of ubuntu and winXP Pro.
The system is a Presario 2175US laptop with a reported 448MB RAM, that hasn't really been altered from the manufacturers initial configuration.  So, it has a XP and XP setup option at boot.  Since the pc is a little aged, it would greatly benefit from a fresh windows install, and I would very much like to get my feet wet with Feisty Fawn.  So, I'd like to properly partition the hard drive first, install XP, install FF, and go from there.  I'm not new to partitioning either, but I want to do a non-standard install of both XP and FF.  I'll explain...
I want my Profiles(Documents and Settings) folder for XP to reside in its own partition, and I would like a separate /home partition for the ubuntu install.  That, I think, would be outlined as such: part1-XP-NTFS, part2-Profiles-NTFS, part3-shared-FAT32, part4-/home-ext3, part5-ubuntu-ext3.  Please tell me if that ought to be different.
If it is right, I want to partition my hard drive(37GB) first.  I want to do so in order to do an nLited XP install with D:\Profiles substituted for C:\Documents and Settings. (note: I don't expect any help with the windows portion of this plan, though I welcome it if anyone has any.)  I would like to follow the first step of partitioning with clearing the present data and installing XP.  This is so that I can access the internet if I have questions or concerns.  Also, it will still be the primary OS for the other users of my laptop.
Third step seems to be the installation of Feisty Fawn--I presently have a copy of the LiveCD.  I do want the system to be dual boot, and would like the system to default boot to XP after 5 seconds or so.  I have no experience with GRUB, but I have some experience with BootIt NG.

I think that pretty much outlines it.  I hope it was thorough enough.  Now, if anyone could offer some advice or bits of instruction, that would be fantastic.  Thanks in advance.

---

### Post by eltorodeoro on 2007-05-08
First, I think I speak for the community when I say:

"Rip it off like a band-aid!"

But who am i kidding, i dual boot too.  I just make it a point to try to do things in Linux rather than MS if i can.

Anyway.  Dual booting can be tricky, but there are plenty of faqs and whatnot here and elsewhere.  Install xp 1st, set up your c: and d: and fat32 partitions the way you want them, and let gparted handle the rest.  you can interact with gparted various ways during the install, including dedicating a partition to /home.

GRUB is easy, and as long as you're dealing with only one hdd, you should not encounter any problems.  the options for the grub screen can be tweaked by editing /boot/grub/menu.lst using vi or gedit or whatever.

feisty is great.  i have a non-standard setup that gave me some headaches at first (rare for ubuntu installs), but its been worth it.  best release to date.

---

### Post by rich.bradshaw on 2007-05-08
2 things that might make you rethink your partitioning:

1) You can easily read and write NTFS using Feisty (get ntfs-3g, has a graphical setup one click and it's done)

2) You need some swap - around the same amount you have of RAM.

nlite is awesome, I used to use it all the time when doing Windows installations.

Grub has a line near the top called default. If you change that it will boot the other things in the list instead of Ubuntu, this is exactly how I have my PC. Boots Windows after 5 seconds, unless I tell it otherwise.

I would do:

1) Windows OS - NTFS
2) Windows Files - NTFS
3) Ubuntu OS - ext3
4) Ubuntu Swap- swap
5) /home - ext3

---

### Post by divorcetheworld on 2007-05-09
Thank you both.  Now I have some direct questions.  Is there any good reason to wait to establish the Ubuntu partitions until after I've done the fresh XP install?  And, while I am reading up on the NTFS-3G project, I would like to ask if there is anything you believe is essential to know before using it?  Or is there something you learned since starting to use it that you think might be either important or useful or valuable to me?  Thanks again.

---

### Post by divorcetheworld on 2007-05-09
Doing some thinking here, and I was wondering if I might do all of the desired formatting right now with only XP installed, then install Feisty Fawn, get any kinks worked out, then wipe the XP partition and do a fresh install of XP.  Is this entirely possible or not?

---

### Post by Nekiruhs on 2007-05-09
Personally, Id install Xp first, then Ubuntu because XP will overwrite the MBR, killing GRUB.

---

