---
title: "Can't resize Windows partition"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by ThierryT on 2007-07-28
Hello! This if my first post and I'm a Linux virgin, so be gentle ;-) 

Before I start, here's my current setup:

Windows XP SP2
Athlon64 3000+
1 GB Ram
2 Hard drives
- Maxtor 160 GB (drive C)
- WD 400 GB (drive E)

I defragmented both discs before starting the installation. 

I decided to try out Ubuntu. I'm trying to install Ubuntu 7.04 desktop 32 bits. I want to 

dualboot. Preferably, my Ubuntu partition (about 20-25 GB would be enough for starters, I 

guess) would be on C: I have a lot of TV shows and movies on drive E and they would be a 

pain to backup. 

Ok, so I start the installation. At step 4, it asks me how I want to partition the disk. The 

first option is 

- Guided - resize scsi2 (0,0,0), partition #1 (sdb) and use freed space.

I don't understand why it proposes only to use my 400 GB drive. Why not my 160 GB drive?

I selected it anyway. I have to admit here that the slider confused me for a second. "New 

partition size" could mean "size of the new partition you want to create" or "new size of my 

Windows partition". I assumed it meant the second and I put the slider at 90% (333.3 GB). 

What can I say, I'm foolhardy!

But it didn't work. Here's the error message:

"Parted can't resize partition managed by Windows Dynamic Disk."

And then I had another error message:

"Failed to create enough space for installation: The resize operation did not create enough 

free space for the installation. Resizing may have failed. You will have to set up 

partitions manually."

So what should I do?

- Do as the document "WindowsDualBoot" suggests? Download the System Rescue CD ISO image and 

resize my partition with it? I'm asking because I'm not sure that document is 100% up to 

date.

- Or should it resize my partition manually? If so, how do you I proceed? All the documents 

I read assumed that you know what you're doing. And its not my case.

Thanks!

---

### Post by sad_iq on 2007-07-28
Well first boot to windows and check your drives for errors...then do a manual partition(or try at least...to see how it is...it's not that scary). I allways do the manual one...if I screw it up...it's my fault...if gparted does it...it's worse Also as a last resort you could phisicaly unplug your second harddisk...just to make sure you don't screw that one up...loosin windows=acceptable...loosing years of work= A BAD THING!!! You could also use Gparted LiveCd .. it works better!!! [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

 P.S. When you select manual partition there is a button(or whatever) in the right upper corner that will allow you to select witch hdd to use. Also make sure the drive is defragmented, checked for errors, and has plenty of free space before you try this!!!

---

