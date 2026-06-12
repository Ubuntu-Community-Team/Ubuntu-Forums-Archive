---
title: "Install on multiple drives"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Psych77 on 2007-09-12
Hi, I've searched the forums and found a few similar threads, but nothing exactly like what I need, so hope someone can help.
Currently I have 2 x 250GB HDDs (not RAIDed).
Drive 0 is XP, Docs & Settings, few apps, about 50% full.
Drive 1 is NTFS format, with just my games installed, and a few backup files, but only about 20% full.

I have a 3rd drive (an old 20GB IDE) to install, which I was going to put Ubuntu on (I presume I'd want to partition into a /home for future clean upgrades, a main /ext3, and a /swap?) .  I would then partition Drive 1 in two, leave 50% as is for my games, format the remainder as FAT32 for shared data.
Can someone please advise the steps to do this (and if this appears to be the best option), and to ensure I can select to use either WinXP or Ubuntu on boot?  I get as far as manually installing the new drive and formatting to clean off the crap already on it, then booting from Live CD!

Thanks

---

### Post by 505 on 2007-09-12
Boot into the live CD and run the setup. There are some questions about partitioning. Choose 'advanced' (or something like that) there. You can then create partitions using GParted right from the installation. This also allows you to set up a seperate /home partition. Then continue with the installation. Grub will be installed so you can dual boot. After installation, open GParted to split drive 1 and format that as FAT32. You can then add this partition to you fstab file so it is mounted automatically.

---

### Post by Psych77 on 2007-09-12
Thanks 505.  
I'm going to knock off work early and go try this now, however 
"You can then add this partition to you fstab file so it is mounted automatically. " 
means absolutely nothing to me!  Could you put this into baby-talk for me please?

---

