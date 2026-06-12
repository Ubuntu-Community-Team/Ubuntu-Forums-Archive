---
title: "Gparted killed my partition table"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Mr_Junebug on 2007-02-16
I seem to have corrupted my partition table on my hard drive.  I had decided to install Ubuntu 6.10 as a dual boot on an existing Windows XP system.  I did the same thing to another machine two weeks ago successfully.

The hard drive is a 120Gig Maxtor.  All 120 Gigs was allocated as an NTFS drive.  So first, in Windows I defragmented the drive.  Good so far.

Then I booted a live version of Ubuntu 6.10.  Everything is great.  I load Gparted and resize the NTFS to 39 Gigs.  Everything is great.  I then add a FAT 32 partition of 39 Gigs, and a Linux ext3 Partition of 38Gis, leaving 995 megs which I allocated as a Linux Swap file.

So I tell Gparted to go ahead and partition this drive.  It chugs away for a few minutes, then tells me part 1 of 4 is done.  In a couple more minutes, it shows 3 of 4 parts done (just the swap left).  It chugs along and then says it had errors partitioning the swap drive.  It then starts looking at the drive again and suddenly come up and shows the entire drive as unallocated.  And now, it will not let me add any partitions.

I closed Ubuntu and tried to boot Windows...dead...no hard drive found.  I load Knoppix.  I try QTparted...same deal.

I read on the forum about TestDisk.  I load it into Knoppix.  It runs and says it can’t read the partition table.  But when it analyzes it finds my three partitions (NTFS, Fat32 and Linux).  But it either tells me the fat32 and the Linux should be 16 sectors, or tells me the NTFS should be 255 (depending on which I have selected).

I try writing a new partition table but it comes up with a error that it can’t write  the partition table.  I tried deleting the old partition table...no go.

TestDisk can see the files in the NTFS partition so they are still there, it’s just the partition table that is scrambled.

Two things. 
First,  I would like to get the data back although I could probably recreate what’s there.

Second, how can I get this hard drive to come back to life and be useful again?  A low level formatting?

Thanks for your help...

---

### Post by go2dell on 2007-02-16
Let this be a lesson to everyone, including me:  ***always*** back up any important data before you go messing around with the partition table!

The problem with not finding a hard drive is that the computer probably can't find any kind of boot loader on the hard drive, at least not where it's expecting to find it.  Your hard drive is definitely NOT trashed, although I'm afraid your data might be.

The first question you need to ask yourself is:  how badly do you want to get back what was there?  If it isn't worth it to you to spend the time, then you may as well set everything up the way you like now and be done with it.  OTOH, if you really do want anything back from your Windows install, I would suggest that you DON'T touch the drive again until you've exhausted other possibilities.

Since you've tried repartitioning with GParted, and then you rewrote the partition table using TestDisk, I'm afraid you may have eliminated any chance at recovering your existing partition table.  I've never used TestDisk, so I can't be certain about that.  Someone else may have a better idea of how to recover from where you are currently.

If you decide to start over from scratch (are you sure you want to do this? ;-) ) then you won't need to do a low-level format (you can't anyway -- such a thing hasn't really existed for end-users since the late '80s).  You can just
```
dd if=/dev/zero of=/dev/hda bs=512 count=1
```
from a Knoppix terminal (substitute the letter for your drive after "of") and it will look to everyone as though you have a brand new drive.  The "if" part is "input file" and the "of" is "output file;" just remember that everything in Linux is a file and you'll understand.  Now you can use fdisk or Gparted or whatever you prefer to partition as you see fit.

I've been in similar situations myself, and I know the sick feeling you have in the pit of your stomach.

Good luck!

---

### Post by aum11 on 2007-02-19
I also have just  had the gparted live cd stuff up the 4th stage of changing sizes in partitions, giving me the message that the whole HDD is now unallocated.  Have had to recover using backups, thank God!

This is the second time in a couple of months that Gparted has been the cause of corruption of my data.

The lessons learnt are:

- always backup before playing with partitions

- don't use gparted until it has improved.  I will be using Nortons Partition Magic which has never caused me any dramas.

AUM

---

