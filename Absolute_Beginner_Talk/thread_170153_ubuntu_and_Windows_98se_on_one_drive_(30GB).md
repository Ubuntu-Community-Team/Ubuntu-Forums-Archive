---
title: "ubuntu and Windows 98se on one drive (30GB)"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-05-04
I currently run Windows 98se (OH MY GOD) on my system and want to add Ubuntu as my main operating system. Is it possible to do this on one 30gb disk allowing both to share a common data area.  I want to do thid since wine does not runn all the programs I want to run.  

Alien Explorers

---

### Post by alienexplorers on 2006-05-04
Any and all help would be appreciated........

---

### Post by jdackle on 2006-05-04
Yes, you perfectly CAN do that!

And it's pretty simple actually!
But not THAT simple!!! Meaning... To help you I need to know a few things...

1. Have you **already installed Ubuntu?** if you didn't, great! DON'T do it just yet, as it is during Ubuntu's installation process you will do most of the work...
2. What do you know about **partitions**?
3. What do you know about **file-systems**?
4. What do you know about **mounting and working with mounted file-systems**?

This are all just basics, really... Just so I don't repeat what you already know... ;)

---

### Post by non-used user name on 2006-05-04
well...

first of all:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

there u will find quite good explained an with pics how to make a dual boot an the information u need about filesystem an pre-installing u need, just follow the gide, read it carefully an in case u dont understand anything or have somekind of trouble just turn back.

make sure that u already backuped all your necesary information, that is quite important so i say again make sure u backup it all!

---

### Post by confused57 on 2006-05-04
Might want to check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=170152](http://www.ubuntuforums.org/showthread.php?t=170152)

No offense, alienexplorers, you'll probably get more responses in this section.
Just wanted anyone replying to see what had been suggested to avoid duplicating suggestions from the other thread.

Be sure to defrag your win98, possibly a couple of times, before you install Breezy for dual-booting.

---

### Post by jdackle on 2006-05-04
Confused57 is right! Posting the same question in different threads is NOT a good idea... You'll end-up loosing more time...
First of all because it will make you go around different threads looking for the answers. Second because it will make you go around screening the info you already got somewhere-else. Third it will make US repeat what someone-else already said. Last but not least, some people, understandably so, do NOT like to see that and might refrain from  posting...

To make it short regarding your question, this is waht you have to do:
1. Defrag W98 (so that all its files are on the begining on the disk, leaving the free space continuous to be used for other partitions. THIS IS CRUCIAL!)
2. Partition the disk - the Ubuntu installation process can take you there. Dual-boot takes at least two partitions (one for Windows, another for Linux). You will need THREE (Windows + Linux + Shared). The shared one must be of the FAT type (readable and writable by both Windows and Linux), as Windows can not access Linux partitions trasnparently.
3. Is more or less included in the former point - setting up dual-boot.

The links you have been provided with should help you do all of that. ;)

---

