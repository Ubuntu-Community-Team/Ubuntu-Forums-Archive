---
title: "Partition problem"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by question on 2006-03-13
Ok. I have a little question...

I have a 200GB Hard drive with XP on it. I take my ubuntu install CD and try to resize the windows partition, but it doesent resize. It just doesent do it even though I tell it to resize it into 40GB.

I want to have 40GB for windows, 19GB for linux, 1GB for swap, and the rest for data. Oh, and the drive is NTFS.

Any ideas whats wrong?

---

### Post by Zelut on 2006-03-13
Linux isn't (safely) able to resize or write-to an NTFS partition.  That makes things a real pain when Windows installs are set to NTFS and you want to dual-boot.

If its an option you could re-install Win & use FAT32 (this way Linux has write-permissions to the partition) and limit it to 40G at that point.  Then, when you install Ubuntu again you can use the remaining space w/o problems.

Some others may have tips as far as editing NTFS.  I haven't dealt with it myself.

---

### Post by question on 2006-03-13
Oh... Well, thats a real bummer, but thanks for telling me :)

And no, I cant reinstall windows at the moment :/

Do you know any good windows software for resizing it? Then ill use the ubuntu partitioner to make the linux partitions and a big shared fat32 partition.

---

### Post by Zelut on 2006-03-13
For windows I have used Partition Magic and it worked fairly well..

If you can get the windows partition resized and leave the empty space you should be set.  NTFS is a real bummer ;)

---

### Post by question on 2006-03-13
Ok, thanks, ive heard about that but ive never used that. Ill try it :)

And yea. I wish microsoft would really open up NTFS. Im not as microsoft hating as everyone else, but I am not happy at that :/

---

### Post by nalmeth on 2006-03-13
DEFRAG YOUR WINDOWS PARTITION THOROUGHLY! then partition it

good luck!

---

### Post by question on 2006-03-13
> DEFRAG YOUR WINDOWS PARTITION THOROUGHLY! then partition it

Yep, I did. Though it didnt need much defragging - I only got the computer a couple hours ago ;)

> good luck!

Thank you :)

---

### Post by Zelut on 2006-03-13
If you just got it a few hours ago & dont have hundreds of things to backup & restore I'd say re-install and use FAT32.. but thats just me ;)

Again, have fun.

---

### Post by question on 2006-03-13
Yea, I probably would do a clean install, but my computer didnt come with an install CD. I could if I really needed to, but its just easier to keep windows legal.

But thanks for your help :)

*cant wait to get back on linux*

Ok, I am now defragging, then I am gonna use partition magic, then install linux :D

Or... Not. Partitionmagic didnt work o_O

---

### Post by Zralou on 2006-03-13
If you can get your hands on an XP install disk, I think you can run the install/recovery and it will resize the partition.  Been a while since I messed with XP, so I might be wrong!!!. :-k 

Sara Lou

---

### Post by taurus on 2006-03-13
[QUOTE=question]
And yea. I wish microsoft would really open up NTFS. Im not as microsoft hating as everyone else, but I am not happy at that :/[/QUOTE]
Open up NTFS!!!  Yeah right, not in your life time...  Didn't they even try to patent fat32 filesystem but was turn down?

---

### Post by question on 2006-03-13
I have an install disk... How would I go about resizing it?

Ive been messing around with alot of partition programs in the last hour or so and none work at all :(

> Open up NTFS!!! Yeah right, not in your life time... Didn't they even try to patent fat32 filesystem but was turn down?

I know they wont. But it cant hurt to hope ;)

Maybe if Ballmer gets fired.

---

### Post by AtinLango on 2006-03-13
Have you tried Gparted or QTParted? They should work very well even if you have NTFS. Be sure the defrag has been done well so there is no data at the end of the partition.

---

### Post by question on 2006-03-13
[QUOTE=AtinLango]Have you tried Gparted or QTParted? They should work very well even if you have NTFS. Be sure the defrag has been done well so there is no data at the end of the partition.[/QUOTE]

Those are linux applications. I am trying to do this so I can install linux (and to have a partition for my data away from windows) =P

---

### Post by nalmeth on 2006-03-13
Do you have a knoppix or an ubuntu liveCD?
I think they both have gparted

If not, hopefully you've got a fast net connection and won't take long to download

---

### Post by question on 2006-03-13
I started to download knoppix and it went at 300KBps+, which is a good speed. But then I stopped because I didnt know if it would work on my hardware.

So, ill just try it anyway. Downloading now :)

---

### Post by nalmeth on 2006-03-13
I think that of all distro's knoppix is most dependable with hardware.. My experience anyway..
I was just hoping you don't have dialup! I can't believe how many people still do

---

### Post by AtinLango on 2006-03-13
[QUOTE=question]Those are linux applications. I am trying to do this so I can install linux (and to have a partition for my data away from windows) =P[/QUOTE]

There is a live GParted CD on its own and QT Parted can be found on Knoppix or RescueCD. All these CDs run on their own irrespective of the OS you have.

---

### Post by question on 2006-03-13
> There is a live GParted CD on its own and QT Parted can be found on Knoppix or RescueCD. All these CDs run on their own irrespective of the OS you have.

Yea, forgot about live cds :P

I accually didnt think the ubuntu live CD had gparted, as the installation cd doesent.

> I think that of all distro's knoppix is most dependable with hardware.. My experience anyway..
I was just hoping you don't have dialup! I can't believe how many people still do

Yea, its amazing how people still have dialup. I mean, thats not an internet connection... Thats just a method to view web pages ;P

Heh. I just reinstalled windows :/

I did it to a 37GB partition. It only let me use NTFS, but heh. I still have the rest of the space partitioned :D

---

### Post by Niels13 on 2006-03-14
This may be a bit late, but with miniPE you could have resized it.

[http://jacksonian.ca/brian/info/miniPE.htm](http://jacksonian.ca/brian/info/miniPE.htm)
[http://www.mininova.org/tor/56309](http://www.mininova.org/tor/56309)

It's a live cd with a customised version of windows on it that loads a truckload of tools, including multiple partitioning tools. And cause it is windows, it can alter ntfs.

This may be helpfull in the future.

---

### Post by nalmeth on 2006-03-14
Yeah, I don't think the windows installer will let you choose fat32. You have to create one manually first, then tell windows to install itself there

---

