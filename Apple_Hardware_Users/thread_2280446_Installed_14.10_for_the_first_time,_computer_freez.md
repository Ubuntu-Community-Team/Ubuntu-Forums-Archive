---
title: "Installed 14.10 for the first time, computer freezes on bootup - 2009 MacBook"
date: 2015-05-30
forum: Apple Hardware Users
---

### Post by Fasmer on 2015-05-30
Hey guys, I'm fairly new to Linux in general. I have an old 2009 MacBook sitting around that can barely work as it is, so I thought what the hell, I'll try putting Ubuntu on it. I backed up all my data, cleared the harddrive for no partition to make Ubuntu the primary OS, and installed from a flash drive. 

It seems to have installed fine, but whenever I attempt to boot up the computer it freezes. Not always in the same spot either, sometimes it seems like it gets further than other times. I'm wondering what real options I have to fix this? Any help would be greatly appreciated.

---

### Post by coffeecat on 2015-05-31
Welcome to the forum. I've moved your thread to the *Apple Hardware Users* section so that those with experience of Apple hardware can help. I've edited your thread title to mention the Macbook you are using - always choose a thread title which will attract those with relevant experience.

A few initial thoughts for you. Ubuntu 14.10 will go end of life in July 2015 - no more updates after then. I suggest that if you want to install Ubuntu on that machine you try with either the latest LTS (long-term support) release which is 14.04 and which doesn’t go end-of-life until April 2019, or the most recent release, 15.04, which has only 9 month's support, ending in January 2016. You can download ISOs for both the 14.04.2 point release or 15.04 from here:

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

Did you check the md5sum on the 14.10 ISO that you used to create the bootable flash drive? It's possible the ISO was corrupted on download. Check the ISO of any new download. Details here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you download from the first link, you'll find the relevant MD5SUMS on each of the 15.04 and 14.04.2 pages.

---

### Post by Karl_Hungus on 2015-06-08
I may have a solution... do you know what your GFX card is good sir?

---

### Post by Karl_Hungus on 2015-06-09
try installing using a DVD-ROM not USB should force (Legacy/bios) after you install use the proprietary drivers and you should be fine.

---

### Post by maclenin on 2015-06-18
My two cents:

[http://ubuntuforums.org/showthread.php?t=2259849](http://ubuntuforums.org/showthread.php?t=2259849)

Good luck!

---

### Post by davidchute26 on 2015-06-19
How much RAM does it have? As rough guide 14.10 needs at least 1GB RAM. It could be freezing because it ran out of unallocated memory. Try Xubuntu or Lubuntu if this is the case.

---

