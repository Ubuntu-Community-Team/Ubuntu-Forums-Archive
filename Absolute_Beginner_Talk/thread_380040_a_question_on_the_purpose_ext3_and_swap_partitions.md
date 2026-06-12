---
title: "a question on the purpose ext3 and swap partitions"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by ensignmessink on 2007-03-09
I have just created a 1GB swap and a 6GB ext3 partitions on my harddisk in order to install Ubuntu, however, am I correct in that I have to install Ubunty itself and any other programs in the swap partition and that ext3 partition is merely for data storage? Please tell me wether I'm wrong or right on this one.

---

### Post by benfindlay on 2007-03-09
Basically the swap partition acts as extra RAM and memory for the computer to use, much the same way as WIndows uses a Page File. Your installation goes into the ext3 partition that is labelled with a / (meaning root).

You can add extra partitions and label them as you like. It is quite common practise for people to mount their /home partition on a separate drive, as reformatting will not lose your user data that way.

Hope this helps!

---

### Post by Crooksey on 2007-03-09
Yes, the swap partition acts as extra or supply RAM, but its no-where near as fast, if you have more than 1GB or ram you will probably never use the SWAP.

The / partition is called the root filesystem, if you just have one partition this is where everything for your Ubuntu install will be placed, installed programs and user settings.

Many users like to have a separate /home partition, so if they change Linux distro's they keep the same home partition and just format / to save their data.

Ext3 is just the filesystem type, like FAT32 on windows, the alternative is ReiserFS (NTFS on windows), thats the best way to understand it.

---

### Post by pveith on 2007-03-09
Keep in mind that swap is used for suspending in Ubuntu. So you actually need more swap than memory (a rule of thumb is to have swap double memory). So if you want to do memory intensive tasks like transcoding really big pictures you will probably end up needing swap (i build a 40 page PDF A4 comic with 300dpi and it was a really huge chunk). But mostly i use swap for suspending only...

---

