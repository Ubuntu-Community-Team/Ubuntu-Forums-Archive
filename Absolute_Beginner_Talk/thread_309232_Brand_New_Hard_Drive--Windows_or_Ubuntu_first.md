---
title: "Brand New Hard Drive--Windows or Ubuntu first"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by bkthiess on 2006-11-29
Sadly, and luckily, the hard drive in my laptop died.  I have ordered a replacement, and in the meantime discovered the ubuntu live cd, which allows me to work on my computer without a hard drive!  That freaking rocks!

Here's my question:  When the new drive comes in, I need to install Windows XP on it (for video editing and work-related issues).  However I would like to have Ubuntu on it as well.  Do I install Windows first, and let windows create a partition on which to install ubuntu later?  Or would it be better the other way around.

Thanks, from a newbie!

---

### Post by taurus on 2006-11-29
Install XP first and make sure you create two partitions, one for XP to install on and leave the other one alone.  Then, tell Ubuntu installer to use the second partition and it knows how to handle it from there.  Make sure you install GRUB on MBR so you can boot XP and Ubuntu when you turn on your laptop.

Good luck.

---

### Post by nickburns on 2006-11-29
You can always go with Ubuntu and vmware

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

### Post by ajgreeny on 2006-11-29
Definitely install windows first, then ubuntu.  You could always,, if you wanted download gparted liveCD and partition the drive before you start into a windows partition and a ubuntu partition, but it is not really needed as the ubuntu partition can be made using free space on the drive when you install ubuntu.  That is what I would do.

Enjoy!  Ubuntu is great.

---

### Post by bkthiess on 2006-11-29
Thanks everyone.  Sounds like windows first.  The new hard drive is 60G.  Will a 10G partition be enough?

I edit video (albeit this machine just barely meets video editing specs--but I digress) and need alot of hard drive to store the raw avi's (about 13G per hour).

Anyone know if 3 partitions would be best in this case? (Windows, Ubuntu, and blank-regularly-defragged space)

Thanks again!

---

### Post by oskar.hansen on 2006-11-29
uh I just installed vmware - works perfectly for me. Don't know if it's going to fit with video editing though.

But my setup right now is, as you sugest, 3 partitions. On a 40G drive:
10 for my ubuntu; I still have 4G free
20 for 'data' (everthing that is not related to OS')
8 for Windows; this is not enough for me I only have 5mB left. (Autocad, Mathcad and OOo installed)

The data drive is ext3, just google for drivers to windows. I believe it works better than the oldish fat32 drives. At least it allows bigger filesizes.

Enjoy :)

---

### Post by birchwood on 2006-11-29
10 gigs will definitely be enough for a Windows XP installation with video editing apps and other utilities.

---

### Post by Aranel on 2006-11-29
It may be a good idea to create a third partition for storing music. Linux can read FAT32 just fine, but NTFS hasn't been perfected just yet (although it's making progress). Of course, you could use FAT32 on your Windows installation itself, but...*shrugs*

---

