---
title: "Partition problems with Fiesty. Arg."
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-05-24
I had edgy and windows 2000 pro loaded on one 250 gb drive. I had windows first @ 26gb partition, then 512mb swap, then 204gb ext3 linux.

What I did when I installed fiesty was I formatted the ext3 partition only. When I booted up, I got a grub error 22 for linux, grub error 13 for windows. Can't boot to anything now. (I'm on the livecd posting this).

So I'm trying to reinstall fiesty in the right fashion. But I get an error. My goal is to do this.

Windows NTFS 26gb (Left alone)
Linux SWAP 768mb (Need to create)
Linux EXT3 204gb (Need to create)

I can set up swap fine. But whenever I add the EXT3, I get an error. It says "Can't have the end before the start!" 

What's this mean? I've tried every combination available with swap and EXT3. I'm lost.

What should swap be? Logical? Primary? Beginning? End?
What should ext3 be? Logical? Primary? Beginning? End?

I'm lost.

---

### Post by Roasted on 2007-05-24
Been sitting here for the last half hour praying I'd get a response before I go to bed. :(

---

### Post by ayenack on 2007-05-24
You should be able to recover your MS2000 Pro partition with the 2000 disk without loosing any important data other than a few drivers for graphics cards etc. If you have no important data on the Ubuntu partition you can use the live CD again then GParted (System>Administration>GParted) in the live CD to partition the drive the way you want.

You will need a swap  partition of about 2GIG (I use five on my PC but that's is overkill for most users)
If you want just one big drive of 202GIG you can. Both the swap and the ext3 partitions can be extended as far as I know this should not be a problem. You should not format your NTFS file system as I'm sure you know. And all partitions should be at the beginning both swap and / (root).
Don't forget that if you have just one drive of 202GIG this will be the root partition. On this Partition you will only be able to write to your home directory unless you change permissions (not advisable). To write to anywhere else on the drive you will have to log in as root.

Best of luck. ayenack.

Just missed you before you went to bed.

---

### Post by Ek0nomik on 2007-05-25
As far as Swap is concerned, he probably wants 2x his RAM.

I made all of my partitions as Primary.

---

### Post by Roasted on 2007-05-25
I'm in gparted.

NTFS is left alone.

I can create 2gb of SWAP.

I cannot create the remainder as EXT3.

It just gives me an error and said unable to create.

Why?

---

### Post by Ek0nomik on 2007-05-25
Have it look like this:

|------NTFS-------||-------EXT3-------||---Swap---|

All as Primary partitions?

(Also, did you make sure to defrag in Windows so your data is at the front of the drive.)

---

### Post by Tomjeep on 2007-05-25
I think you can just leave that space without format, and ubuntu will pick up that blank space and use a small part to create a swap partition and the rest as the root partition

At least that is what i used to do a few years ago, and it will let ur NTFS partition as it is now

---

### Post by Roasted on 2007-05-25
WTF!!!!!!!!! It can't create a primary partition on /dev/sda. This is BS. I cannot fathom what could possibly be wrong with this!

---

### Post by ffderrick on 2007-05-25
You are trying to fit windows into a very small portion of your drive.  Why?  Give it a little more room.  I use a little less than half my drive for windows and the other half I split between two linux distro's and swap.  Ubuntu is my standard and the other I change to check out new distro's.  Try making a smaller ext3 partition to get the install working.   My drive is 160GB.  There shouldn't be an issue with large drives and ext3.  
Whenever a friend of mine has to use a system recovery CD for windows I tell them about linux and Ubuntu.   Consider using your live Cd to save important files and start over.    Write zero's to your hard drive and begin from scatch.  Install windows the size you like and then install Ubuntu on the remainder of the drive.

---

### Post by Ek0nomik on 2007-05-25
The size of Windows has nothing to do with it.  26GB should be plenty if you're just install like 10 applications.  I have Photoshop, Illustrator, Microsoft Office, Microsoft Visio and Civ IV installed on a 20GB partition on my laptop.

Personally, I always like partitioning from scratch, but I don't know why it won't let you touch the drive.

---

### Post by darkworld on 2007-05-25
> 
I made all of my partitions as Primary

Its good practice to give /var and /tmp there own partitions. Check out "Maximun Linux Security" book.

---

### Post by Ek0nomik on 2007-05-25
> **darkworld said:**
> Its good practice to give /var and /tmp there own partitions. Check out "Maximun Linux Security" book.

I don't think most "regular" Linux users do that however.

---

### Post by ayenack on 2007-05-25
In GParted you need to delete the previous ext3 partition then apply changes and then recreate it. Let me know if this works if not post back and we'll try to sort it out.

Best of luck. ayenack

---

### Post by mike_mceldowney on 2007-06-07
Same problem here.  I was trying to partition 2GB for swap and partition the remainder for /.  I was getting the same error.  I then set up a /home with 100GB, and then was able to use the rest for /.  It must be a size limitation of some kind...

Mike

---

### Post by Roasted on 2007-06-07
I ended up setting up 3 partitions. Swap, root, and home. That way if I ever want to upgrade linux I can just overwrite the root directory, leaving everything in home alone. It seemed to work then... but I forget what exactly I did to solve my problem.

---

### Post by MoonDoggie on 2007-08-23
> **Roasted said:**
> I ended up setting up 3 partitions. Swap, root, and home. That way if I ever want to upgrade linux I can just overwrite the root directory, leaving everything in home alone. It seemed to work then... but I forget what exactly I did to solve my problem.

The problem is only for users with 200gb+ Harddrive partitions.  The problem does not affect less than 200gb partitions...I have the same problem.  Please help.

---

### Post by MoonDoggie on 2007-08-23
SOLVED:

I fixed this problem by Installing the UBUNTU ALTERNATE CD instead of the regular one.  For some reason installing in Text mode feels better and the partitioner is not affected by this issue.  Good Luck.

---

