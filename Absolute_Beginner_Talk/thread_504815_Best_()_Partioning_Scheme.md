---
title: "Best (?) Partioning Scheme"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by ChaOConnor on 2007-07-19
Good morning!   I'm wondering if there is a best partioning scheme I should use for Ubuntu.  Here are my requirements and what I currently have.

1 - 320 Gig SATA HD
First Partion - Couple hundred meg FAT 16 partion.  Have no idea what this is.  Came w/ my Dell
Second Partion - Win XP - want to keep a small XP partion. NTFS
Third Partion - Ubuntu - ext3
Fourth Partion - Swap

So my question is this: If I'm willing to blow away my current drive (COMPLETELY), what would be the best way to setup partions?  All of the ones I have are Logical partions so I'm "maxed" out at this point.

If I have 2 Gigs of Ram, how big should my swap partion be?  Should I make a Home partion?  

Basically I'm will to do a clean slate and I want to make sure it's done right.

Thanks!

---

### Post by steve.horsley on 2007-07-19
Don't blow away the first partition - it will be the dell utilities - hardware tests and the like that they may ask you to perform if you report a problem. It may even have a windows recovery feature (otherwise, it wouldn't be that big).

I would advise having 4 partitions:
1 * 10G to use as /, for the system.
1 * 10G to use later, as / for the next version system
1 * 1-2G swap
1 * the rest, for /home.

Having two system partitions allows you to try out upgrades without trashing your current system.

---

### Post by punx45 on 2007-07-19
general convention says that swap should be 2x RAM, however, that was set many years ago, and I am wondering if a 4GB swap partition is excessive, but it probably cant hurt (especially since the HDD is equally large).

a separate /home partition isnt necessary, and I dont think the general user will find much use for it.   I had one at one point, but no longer do.   of course, on that system, all my pertinent media is on another disk altogether.

---

### Post by ChaOConnor on 2007-07-19
So what about a Windows partion?  

Any advice on Logical vs Extended partions?

Thank you both!

---

### Post by jasonlfunk on 2007-07-19
The main reason you would want a /home partition is:
1) You reinstall your root filesystem a lot. Perhaps for distrubution changes/upgrades, screwing around and breaking things, etc.
2) You format it in FAT32 and let windows read it for music/pictures/etc.

---

### Post by misfitpierce on 2007-07-19
I have mine set to...
99 gig to /
1 gig to SWAP

I realize from what others say about it should be 2X ram but with compiz-fusion running and all I still dont use my ram up and SWAP rarely ever goes above 60MB used. So its really up to you 1-2 gig SWAP is a good idea and a seperate /home/ partition is not necessary a simple single to / will do just fine.

---

### Post by ChaOConnor on 2007-07-19
Woah!  Wait a minute, you just blew my mind!

The home partition can be FAT 32?  Linux is cool w/ that?

So wait, Linux root / is ext3?  /Home is Fat 32?  Swap is Swap and Windows is NTFS... WOW!

This solves my problem w/ sharing my music between Windows (iTunes) and Linux.

---

### Post by punx45 on 2007-07-19
> **ChaOConnor said:**
> So what about a Windows partion?  

Any advice on Logical vs Extended partions?

Thank you both!

I would set the Windows partition as small as you feel comfortable with, as you said you wanted it small.   maybe around 20 GB?

as for Logical vs. Extended:

to quote [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018) 

> Primary, Extended, and Logical partitions.

Primary partitions: The original partitioning scheme for PC hard disks allowed only four partitions, thus you are allowed up to 4 primary partitions. Linux numbers primary partitions 1-4.

    Note: Some OSs (Windows, BSD) can ONLY be installed into a PRIMARY partition.
    Linux (and swap) can be installed into a primary or logical partition.

Extended and Logical partitions: To overcome this limitation, extended partitions are used. A single primary partition may "converted" into an "extended" partition which is then further divided into sub-partitions called logical partitions. Sorry you may not convert more then 1 primary partition into an extended partition. You then create logical partitions within the extended partition. It may be possible to create further extended partitions within an extended partition, although this becomes complicated and I am not sure of any advantage this offers.

Linux numbers Logical partitions starting with 5: The numbers 1,2,3 and 4 are reserved for the primaries, even if you have just one primary partition. So if you make one primary partition and one extended extended partition with one logical partition:

The primary would be hda1
The entire extended partition (and any logical partition(s) it contains) would be hda2.
The logical partition within the extended partition would be hda5.

---

### Post by alienexplorers on 2007-07-19
I use 10GB for root
For /home I use 20GB
For /backup I use 8GB
For /swap I use the rest

---

### Post by lamalex on 2007-07-19
> **punx45 said:**
> general convention says that swap should be 2x RAM, however, that was set many years ago, and I am wondering if a 4GB swap partition is excessive, but it probably cant hurt (especially since the HDD is equally large)..

4gb of swap doesn't /hurt/ but it's a complete waste. any more than 2 you're basically just throwing away those sectors of your hard drive as they will never get used, and if you need 4gb of swap because you swap a lot, then really, you just need more ram.

---

### Post by schorsch on 2007-07-19
> **Iamalex said:**
> 4gb of swap doesn't /hurt/ but it's a complete waste. any more than 2 you're basically just throwing away those sectors of your hard drive as they will never get used, and if you need 4gb of swap because you swap a lot, then really, you just need more ram.
If you use the hibernate mode on a laptop the swap is used to store the content of the RAM, so sizing the swap 1.5 times the size of RAM will be sufficient. The more RAM, the more swap .... for hibernating on laptops only, of course!

---

