---
title: "partition advice"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by fizzychicken on 2007-04-21
Ok so Ive got a reasonable laptop that Ive been thinking of using to try ubuntu/linux for the first time, unfortunatly I still need XP on it due to some work based crapplications I use so Im thinking of dual booting, I have all my cds ready to go and Im confident on instal etc, the laptop is totaly clean and empty and has a 30GB drive in it so I was wondering if someone could please suggest the best partitions for me to generate on it and what FATs I should be using on each. I would idealy like half of the 30 to go to XP and half to Udbuntu.
many thanks.

---

### Post by Happy_Man on 2007-04-21
Hmmm.... 15 gigs for XP seems awfully small. What I suggest is install XP FIRST, and see how much space it takes up with everything you need. Then come back and post with those numbers, and your computer specs.

---

### Post by fizzychicken on 2007-04-21
the laptop is a 2Ghz p4 with 512MB ram and 30GB disk, I have another one of these laptops at work, with XP and all the apps I need  installed on it , it only uses about 10GB as all downloads get put on external storage. So I have 20GB left to play with.

---

### Post by Sef on 2007-04-21
You will need these partitions: XP, Ubuntu, and Swap.  Are you planning on sharing any files between the operating systems?   If you may want a fourth partition to share the files though Feisty has software that can read and write to NTFS, which is what XP runs on.  

I would make XP 14 gb, Ubuntu, 10 gb, and swap 1 gb.   Swap should be double your ram, unless you have at least 1 gb ram, then it could equal it.   You get updates to XP, so you need room for them to install.

---

### Post by fizzychicken on 2007-04-21
Many thanks for your reply, what I need to know (and this is my fault for not being more specific) is what those partitions should be, which should i make as primary, what FAT should they be? does it matter where the bootloader is? Im all ok with the instal and setup of both operating systems but sorting partitions out correctly has got me stumped.

---

### Post by bernied on 2007-04-21
There is no correct. If you will only ever have four partitions, make them all primary. But you don't have to, and by default, I think ubuntu will create a primary for the OS, and put the swap partition into a logical partition (or that's what I remember it wanted to do last time I did an install from a cd). But it doesn't matter, you can put ubuntu on a logical partition if you like, it will boot fine. Same goes for the bootloader (grub by default). These days people are using just one partition for the OS and another for swap space.

When you ask about FAT is that about the filesystem? Ubuntu uses ext3 by default, which works perfectly well. Some folk, when they want to go really fast, might use a different filesystem, because under certain conditions it works just that bit quicker - it's all racing stripes to me. You'd be well advised not to use a non-linux filesystem, like ntfs or FAT16/32 (is that what you meant by FAT?). These will not work so well (or possibly at all)

If this is your first install, just go with the defaults, make life easy for yourself. You don't have to worry about the partitioning, just make some space and let the installer do the hard work.

---

