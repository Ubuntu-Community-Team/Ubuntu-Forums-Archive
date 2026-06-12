---
title: "getting and installing ubuntu dual boot"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by dish_cloth on 2007-06-08
i have a 4200+ athlon and i was wondering should i select that i have a 64bit AMD for downloading ubuntu or just select standard?  And what does selecting that do, is there a 64bit version of ubuntu, if so is it different and how? 

secondly I have 2 internal hard drives, 1 i just run my OS off of and games i want to run well 80gig raptor, and my second drive is just a storage drive, id like to install ubuntu on my system drive which currently has windows XP on it and i want to do duel boot.  Do i have to partion 1 or both of my drives? how do I install for dual boot?

yea i know n00b question, im a total newbie, havent touched linux in 3 years when i played around with red hat 9 on a 166mHz comp

---

### Post by lamalex on 2007-06-08
you can select either, you're probably better off picking the regular 32 bit since there's no 64bit flash, you're not really going to see a bit difference in performance.

You only /need/ to partition the drive you're installing ubuntu onto, but if you wanted you could stick the /home directory, whis is all of your personal files on a seperate partition on the storage drive and the / directory, which is all of the system files, on the raptor. It sounds more complicated than it is but it's probably your best bet.

---

### Post by viciouslime on 2007-06-08
Dual booting will be taken care of by ubuntu automatically so you don't have to do anything there.

There is a 64bit version of ubuntu, but unless you're going to be doing lots of encoding work, I wouldn't bother. The disadvantages far outweigh the advantages for most people at present, though this gap is getting ever smaller.

You will just need to create two partitions on whichever drive you want Ubuntu installed to. Though I would recommend making three. A root partition (the equivalent of C:\ in windows) a home partition (the equivalent of documents and settings in windows, however, unlike windows ALL of your documents and settings will be stored here, so if it is on a separate partition you can always reinstall ubuntu, should something go wrong, and everything will work exactly as before) and finally a swap partition. This is like "virtual memory" under windows. It only needs to be about 0.5gb.

---

