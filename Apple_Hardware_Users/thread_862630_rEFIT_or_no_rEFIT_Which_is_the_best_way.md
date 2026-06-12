---
title: "rEFIT or no rEFIT? Which is the best way?"
date: 2008-07-17
forum: Apple Hardware Users
---

### Post by Mattaus on 2008-07-17
Hi all,

Sorry if this has been posted already as no doubt it has been covered elsewhere (I looked but couldn’t find anything specific enough)

Anyway, I just got a Macbook Pro (3,1) and I would like to install Ubuntu 8.04 on the machine. I will be using OS X for all my Adobe Creative needs (Photoshop, Encore, Premier Pro, After Effects) and then using Ubuntu for everything else like day to day net surfing, word docs etc etc.

I went and looked at the sticky at the top of the page relating to guides for installing 8.04 on Macs, and have been left confused. 2 methods are listed as you no doubt realise - one without rEFIT and one with.

Which is the best method? I can't seem to determine any major differences but then again I'm no software expert. The search I mentioned before really only gave me the impression that rEFIT can cause any number of problems. Is this true?

If anyone could give me some advice that'd be great!

Thanks in advance.

- Matt

---

### Post by Mattaus on 2008-07-17
Sorry, forgot to check instant email notification

---

### Post by DGortze380 on 2008-07-17
If you're going to be using Ubuntu often, install rEFIt.  It does other things (like give you an EFI Shell) but the major difference for you right away will be that when you boot the computer, the first thing to on the screen will be the rEFIt menu with an Apple logo an Ubuntu logo (any other OSs you have), and reboot/shutdown/efi shell options.  You choose your OS and you're on your way.  Otherwise you'll have to hold the option key when you turn the computer on and you'll get apple's hard drive icons one for OS X and one for Ubuntu that will be labeled Windows. Doesn't seem like a big deal, but I can't tell you how many times I turn on the computer and ended up in OS X because I forgot to hold option.

---

### Post by Mattaus on 2008-07-17
Ah cool. Thanks for that. I'll got onto installing it straight away.

---

### Post by kosumi68 on 2008-07-17
There is also the possibility to use refit to sync your GPT and MBR partition tables, which might come in handy if you do manual work on the partitions with old-style tools like fdisk.

---

### Post by blunt.dualboot on 2008-07-17
I would suggest rEFIt even though I am a newbie.

I tried without rEFIt and installation and had some issue. 

Then I followed instruction in section ***"Installing Ubuntu alongside OS X (Dual Boot)"*** in [[COLOR="DarkRed"]this wiki[/COLOR]]("https://help.ubuntu.com/community/MacBookPro").

It's rather straight forward and works without a hitch. :)

Good luck.

---

### Post by Mattaus on 2008-07-17
Yeah thats the exact method I used. I had a few issues after reagrding lock up on the tux logo etc but I fixed them easy enough. Now I'm just trying to figure out how to see the Linux aprtition from inside OS X....it works fine the other way around.

---

### Post by cyberdork33 on 2008-07-18
> **Mattaus said:**
> Yeah thats the exact method I used. I had a few issues after reagrding lock up on the tux logo etc but I fixed them easy enough. Now I'm just trying to figure out how to see the Linux aprtition from inside OS X....it works fine the other way around.
rEFIt is definitely not required, but is recommended.

The lockup on the tux logo is not due to a problem with rEFIt, but rather a bug in the Hardy installer.

There is a ext2/3 driver for OSX. It doesn't work very well, but it should get you access to the Ubuntu partition.

---

### Post by DGortze380 on 2008-07-18
> **cyberdork33 said:**
> rEFIt is definitely not required, but is recommended.

The lockup on the tux logo is not due to a problem with rEFIt, but rather a bug in the Hardy installer.

There is a ext2/3 driver for OSX. It doesn't work very well, but it should get you access to the Ubuntu partition.

My advice would be to either set up a partition to share (NTFS or FAT32 depending on your needs) or use your HFS+ as a share (that's what I did, seemed to work better than the ext2/3 driver in OS X)

---

### Post by Brightbelt on 2008-07-18
Kosumi68 also referred to this I think...

When using rEFIt and installing Ubuntu, when you reboot for the first time and see your rEFIt screen, make sure you use rEFIt's partition editor and sync your partitions. You may have trouble getting Ubuntu to boot if this is not done. 

All you really have to do is go into the editor and by default, it asks you right away if "you want to sync the partitions Y/N ?" Just press 'Y' and that's all you have to do. 

Good Luck.

---

### Post by Mattaus on 2008-07-18
Yeah I had all the issues you guys have alluded to. I worked them thanks to the very helpful guides in the stickies up top.

As for sharing between drives I've got another thread going on that and have pretty much decided on a shared drive.

---

