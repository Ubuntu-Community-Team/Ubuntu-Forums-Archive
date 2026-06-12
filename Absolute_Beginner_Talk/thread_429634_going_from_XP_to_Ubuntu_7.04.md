---
title: "going from XP to Ubuntu 7.04"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by thedatahouse@yahoo.ca on 2007-05-01
So i have a dell pc running windows xp and wish to convert solely to UBuntu. I burned the ISO cd and run the install from the CD. No problem. Now i wish to run Ubuntu from the hard drive and wipe out XP. So I double click on the install icon and it does a few things then just hangs there indefinitely. Am I doing something wrong? Is this the correct method if I don't want to run XP on the machine. i.e should i wipe the drive clean or what. Have not found anything online about converting your windows PC to solely run Ubuntu. Looking forward to any help. ciao

---

### Post by Bachstelze on 2007-05-01
When the Live CD fails, use the Alternate :)

---

### Post by starcraft.man on 2007-05-01
Yup, like hymn said Alternate always works (or should always work). Just burn it to a cd (you can get it [here)]("http://releases.ubuntu.com/7.04/"). You want to use the Text Install when you get the Ubuntu Splash screen, then follow the guided questions until you get to the partitioner. You will likely see an NTFS (or Fat32 if you made windows with that) partition there, just select it and delete it. Then make 3 new partitions:

1) First, should be 6-8 GB and is your root drive, should be formatted Ext3, and mounted as "/". This is where the entire OS will be installed. This is the only partition that needs to be primary.

2) Second is the swap file, it should be 2-3 GB depending on how much space you have, it is simply formatted and does not mount. It should be logical.

3) The last partition should be your home, thats where all your user data will go. It should be Ext3 as well and mounted to "/home". It can be the rest of your drive space. It is logical like the swap file.

Note on home: You don't strictly need to make a separate partition it can just go in the root, we do this so that if you upgrade or downgrade or change versions of your linux distro you can just remount it as a drive easily. If it was in root you'd wipe it every time you installed.

Have fun and spread the word :)

Edit: If you do want to dual boot your machine, resize your NTFS partition so that you have enough space for the three other partitions and then leave it there. Grub will more often then not detect your install of XP unless its corrupt or has a separate boot loader stored locally.

---

### Post by Eric Layne on 2007-05-01
I almost wiped my drive clean in favor of Ubuntu, but thought better of it and decided to keep XP and partition the drive instead. Best decision I ever made! My Ubuntu now collects dust and will be formatted in the near future.

If you are absolutely certain of never needing XP again, format your entire hard drive and run the live cd again.

---

### Post by Josey on 2007-05-01
Keep in mind it's a good idea to burn OS disks at slower speeds.  If your not impatient use 4x.

Did you use "check cd for defects" at the main boot menu?

---

### Post by webjames on 2007-05-01
> **Eric Layne said:**
> I almost wiped my drive clean in favor of Ubuntu, but thought better of it and decided to keep XP and partition the drive instead. Best decision I ever made! My Ubuntu now collects dust and will be formatted in the near future.

If you are absolutely certain of never needing XP again, format your entire hard drive and run the live cd again.

it is fairly easy to run both ubuntu and XP in a dual boot setup there is lots of help on this on this forum. the advantage of this is it gives you a transition stage where if something doesn't work or you find yourself needed to do something that you can't do, you can always do it on xp whilst you learn how ubuntu works. when booted ubuntu should mount (make available) your windows drives so you can access or copy documents from the xp partition to the ubuntu partition, this makes it easy to try out the different programs and how they differ from those of xp. remember ubuntu is free, and you should never need to pay for any software on it, there is normally a free alternative. have a look in add and remove software for all the software currently available!

---

### Post by Josey on 2007-05-01
> **webjames said:**
> it is fairly easy to run both ubuntu and XP in a dual boot setup there is lots of help on this on this forum. the advantage of this is it gives you a transition stage where if something doesn't work or you find yourself needed to do something that you can't do, you can always do it on xp whilst you learn how ubuntu works. when booted ubuntu should mount (make available) your windows drives so you can access or copy documents from the xp partition to the ubuntu partition, this makes it easy to try out the different programs and how they differ from those of xp. remember ubuntu is free, and you should never need to pay for any software on it, there is normally a free alternative. have a look in add and remove software for all the software currently available!

Yes I don't know how many times I was in XP and thought to myself   "I would like to do this..... but it would be such a hassle in windows."  Then boot up ubuntu and I'm doing what I want in minutes.

It's always nice to have alternatives.

---

