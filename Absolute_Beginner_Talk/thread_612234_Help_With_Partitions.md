---
title: "Help With Partitions"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Joeb454 on 2007-11-13
Ok so I bought a laptop that has Vista preinstalled, and it runs really well, as the laptop spec is pretty good.

I've tried the Ubuntu & Kubuntu live CD's (32 and 64 bit) and was thinking of installing, but the laptop already has 2 partitions, the C:\ drive with Windows on etc. and then the S:\ drive, which is a system drive, so I'm not sure what's going on there really.

All I want to know is if anybody could help me figure out what these are, without me having to go and boot in and out of the live CD preferably (not got much time on my hands atm)


And if anybody posts rm -rf / or anything similar, ignore it, because its stupid...that and it has NOTHING to do with this post

---

### Post by bapoumba on 2007-11-13
Please read my sig, last line.

---

### Post by Joeb454 on 2007-11-14
Anybody got any clue?

---

### Post by bigken on 2007-11-14
s:/ is probablys the restore partition to install ubuntu it would be best to create an extended partition and create 

/ 10 gig system  
swap twice your ram ie 512=1gig if you have 2gig of ram dont bother
whats left /home 


use vista to make space for the extended partiton

---

### Post by Joeb454 on 2007-11-14
Ok, just wondering what'd happen if I installed Ubuntu because I don't want to find out that I can't access the recovery partition(s) (yes I think there's 2, one is system files or something :S, probably crap added by the manufacturer but still).

The only reason I'm keeping Vista is because of Uni, obviously the majority of their machines run Windows. So I figured I might need the recovery partitions lol

---

### Post by Inxsible on 2007-11-14
you could also create the backup CDs/DVDs and thn get rid of the partition. That's what i did

---

### Post by stchman on 2007-11-14
> **Joeb454 said:**
> Ok so I bought a laptop that has Vista preinstalled, and it runs really well, as the laptop spec is pretty good.

I've tried the Ubuntu & Kubuntu live CD's (32 and 64 bit) and was thinking of installing, but the laptop already has 2 partitions, the C:\ drive with Windows on etc. and then the S:\ drive, which is a system drive, so I'm not sure what's going on there really.

All I want to know is if anybody could help me figure out what these are, without me having to go and boot in and out of the live CD preferably (not got much time on my hands atm)


And if anybody posts rm -rf / or anything similar, ignore it, because its stupid...that and it has NOTHING to do with this post



Best thing to do is reinstall Vista.  During reinstall you can use the fdisk utility to delete all partitions.  If you know someone that you can borrow their retail or OEM DVD and use YOUR number on the bottom of the laptop that is OK.  After that is done then install Ubuntu on another partition.  

Vista pre-installed is uber bloat ware.

---

### Post by mdpalow on 2007-11-14
I'm thinking the S: drive is probably the manufacturer's recovery partition in case you needed to reinstall Vista at a later time.

When you go to install Ubuntu and get to the partition part find the two listed on there already and don't touch them.

Create a NEW partition with the remaining space and make it / with primary, ext3
then make another partition and name it /home with primary, ext3
then make another partition but select 'swap' instead of ext3 and make it double the size of your ram, but no more than 2 gigs.

As long as you don't touch the other windows partitions, you'll be fine...

---

### Post by bigken on 2007-11-15
> **stchman said:**
> Best thing to do is reinstall Vista.  During reinstall you can use the fdisk utility to delete all partitions.  If you know someone that you can borrow their retail or OEM DVD and use YOUR number on the bottom of the laptop that is OK.  After that is done then install Ubuntu on another partition.  

Vista pre-installed is uber bloat ware.

He might have built in software to create backup discs like Acer and HP provide 

To delete the recovery partition and depend on another persons  vista  is   a very
dangerous thing to do

---

### Post by natehatewindows on 2007-11-15
i would try to make recovery disks, they are much better than the partitions. 

to make room for ubuntu in windows click: **be sure to defragment first**

start >
right click computer>
manage>

when the disk management tool comes up click your hard drive on the left. then find your biggest partition and right click on it and select "shrink volume". a window will then come up that allows you to tell how much you want to shrink it. after this is done you will have unallocated disk space to install ubuntu. When going to install ubuntu be sure to manually edit partitions so you can install in in the right place and if i were you i would for sure make a separate /home.

---

### Post by bigken on 2007-11-15
if do shrink your vista partition this is how I would do it first make your new partition an extented one then do something like this


10gig / (system)

1gig swap ie twice your ram if you have 2gig you dont need it 

whats left /home 

the reason for an extended partition is you can only have four primary partitions 
so if you need a swap and separate home you need to go with an extended partition
this is assuming your going to keep C: & F:

---

