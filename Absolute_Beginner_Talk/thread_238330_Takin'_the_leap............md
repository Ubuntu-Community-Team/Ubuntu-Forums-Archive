---
title: "Takin' the leap..........."
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by saxofoner on 2006-08-17
I'm going to reformat my hard drive with Windows, leave space for the Drake, and finally become the Linux user that I've always been, deep down inside.  My true intentions were revealed to me by the Live CD. 

On my 160 GB Hard drive, how big should the:
Windows Partition
Linux Partition
Swap Partiton
be?

The two OS's will share storage space, right?  Like if I've produced 100 gigs of art in Windows, but the Win partition is only 60, will that art be stored on free space in the other partition?

---

### Post by aysiu on 2006-08-17
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by DevlinP on 2006-08-17
I don't believe that you can distribute between the partitons automatically. I don't think that you can even see the other partition while you are in one. You'll need to do all of the moving manually, or delete some.

But I'm relatively new to Linux.

---

### Post by taurus on 2006-08-17
Depending on how much stuff you intend to install in Windows, 50GB of space is plenty.  So, I would do something like

/dev/hda1 --> XP (50GB)
/dev/hda2 --> share, format vfat/fat32 so you can read and write to it from XP and Linux (50GB)
/dev/hda3 --> /boot (500MB)
/dev/hda5 --> swap (512MB)
/dev/hda6 --> / (whatever left)

---

### Post by saxofoner on 2006-08-17
heh heh, sorry thanks.  Hadn't visited the psycho cats yet.  

But I have two in reality!

---

### Post by sean_ on 2006-08-17
If you're going for half, I'd go for..
80,000mb for windows.
80,000mb for Linux
Swap? I did 512mb.

---

### Post by sean_ on 2006-08-17
> **taurus said:**
> Depending on how much stuff you intend to install in Windows, 50GB of space is plenty.  So, I would do something like

/dev/hda1 --> XP (50GB)
/dev/hda2 --> share, format vfat/fat32 so you can read and write to it from XP and Linux (50GB)
/dev/hda3 --> /boot (500MB)
/dev/hda5 --> swap (512MB)
/dev/hda6 --> / (whatever left)

Also, why are you using 6 hda's?
I just used 3.
HDA1, half of my HD
HDA2, half of my HD (ext3, set my mount point to /)
HDA3, 512mb (SWAP)

---

### Post by saxofoner on 2006-08-17
psychocats said to do the fat32 thing, so they share space.  
Like:
20 for Win
20 for Lin
100 for Fat32  (storage)
and small SWAP

How do you know when to make them logical or primarY?

---

### Post by xmastree on 2006-08-17
I'd do 20GB Windows, 20GB Linux and 120GB FAT32 shared data.
Make one 20GB primary and one 120GB secondary, containing a 120GB logical drive.
Install Windows on the primary, and format the logical as FAT32.
Install linux in the remaining (20GB) free space.

But...

Where will you put your 100GB of art while you're doing all this?

---

### Post by aysiu on 2006-08-17
Well, the Psychocats site actually proposes two main solutions--a shared Ext3 that you use [http://www.fs-driver.org](http://www.fs-driver.org) to read/write from Windows or a shared FAT32 that both can read/write natively.

FAT32 is *one* of the options.

---

### Post by tim.n9puz on 2006-08-17
> **saxofoner said:**
> psychocats said to do the fat32 thing, so they share space.

Definitely use FAT32 and *not* NTFS if you're sharing between Windows and anything else. You can hose an NTFS volume in a hurry if you write to it with anything other than the system that created it.

Tim

---

### Post by saxofoner on 2006-08-17
Think I'll go with xmastree's/psycho cat's option.  
aysiu (is that pronounced:  "I see you"?)

xmastree:  The 100GB of art was a joke/test.  I was saying that if my Windows partition ran out of room, what would happen?

---

### Post by aysiu on 2006-08-17
You can pronounce it however you want.

---

### Post by saxofoner on 2006-08-17
Ha.  Okay.

Hopefully next time I talk to you all, I'll be running Linux off my Hard drive.  Wish me luck!  (If you believe in it.  :-))

---

### Post by aysiu on 2006-08-17
Good luck!

Defragment.
Back up your files.
Don't do anything if you're not sure what you're doing.
Ask any more questions that come up!

---

### Post by saxofoner on 2006-08-17
> **aysiu said:**
> Good luck!

Defragment.
Back up your files.
Don't do anything if you're not sure what you're doing.
Ask any more questions that come up!

I've reinstalled Windows.  Now I'm on the live Ubuntu CD.  I tried to Install, but I was "not sure what I'm doing." 
 
Windows never asked me what should be NTFS, what should be FAT32, blah blah blah.  I just did the C, and the D, and the Install.  I do have 4 partitions now, though.  

Ubuntu asked what to mount the drive thingies, blah blah, and I didn't know what to do.  So I'm asking.  I figured out 
SWAP --> 5GB Logical Partition 7 
and
"/" --> 20GB Logical Partition 5(?)

But I didn't know what to put for the big storage space.  

HELP!!!
[IMG]http://www.freewebs.com/saxofoner91/Partition.jpg[/IMG]
[IMG]http://www.freewebs.com/saxofoner91/Partition2.jpg[/IMG]

---

### Post by aysiu on 2006-08-17
I think Windows defaults to NTFS. As long as you have your partitions in place, you can always change the filesystem on a particular one from NTFS to FAT32 using the Ubuntu partitioning program that comes with the installer.

Note: "changing the filesystem" on a partition will usually erase any data that's on there.

Have you seen this, by the way?
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by saxofoner on 2006-08-17
Yes, thank you for that link.  I just am trying to change them from "unknown" to ext3, and swap.
Would this be good?
[IMG]http://www.freewebs.com/saxofoner91/This%20Right.jpg[/IMG]

---

### Post by MetalMusicAddict on 2006-08-17
> **sean_ said:**
> Also, why are you using 6 hda's?
I just used 3.
HDA1, half of my HD
HDA2, half of my HD (ext3, set my mount point to /)
HDA3, 512mb (SWAP)

Hes not. They are partitions. 3 look to be primary and 2 look to be logical. You cant have more than 4 primary partitions on one drive.

---

### Post by wvslkr on 2006-08-17
As a suggestion;  consider reducing the size of your swap file if you have not allready committed.  You would not likely ever use a swap of that size.  

Wasted space.  Most swap recommends 1 1/2 to 2 times ram size.  I have one gig and very seldom even hit swap.

GL:D

---

### Post by bodhi.zazen on 2006-08-17
I would give Windows a little elbow room, 40 Gb. It is a total pain if C:\ becomes full.

I would use swap = RAM X2. This depends, of course, on your applications. If you run a RAM hungry application you will need swap. If you run out of swap you will crash. If wvslkr down not use swap this merely means s/he infrequently runs RAM intense applications, NOT that you do not need swap.

BUT your current swap is too large.

Ubuntu \ (root) 15-20 Gb is fine.

Rest /mnt/data: FAT32 is likely your best option. Ext3 will work as will NTFS.

also NTFS from Linux works just fine. Have been using NTFS with Windows/Linux share for ? 6 months (yes, both read write)no problem.

Sean_ There are 5 partitions proposed by taurus.

/boot has advantages, but not needed here.

This leaves 4 partitions:
Windows
Ubuntu
Swap
Data

Install away.

---

### Post by saxofoner on 2006-08-17
Wait, wait, wait.  Remember you're talking to a Linux extreme-beginner. 

To simplify what you said:
Lower the swap a bit.  (I've got 2 g ram, so what's wrong with 4-5 Gigs?)

Too late to change windows partition:  I already installed Windows.  Should I redo that?  Is 20 Gigs not enough for Windows XP?  (Nothing else, just XP)

So I mount "/data" (or is it "/mnt/data"?) on the big "storage" (FAT32) partition, and /root on the "Linux" partition, and swap on the "Linux-Swap" Partition?  Does that "Linux-Swap" also act as Windows swap?  [Look at my screenshot.  Will that work, with what you just said?]

Edit:  I changed "Swap-Linux" to 3.9 Gigs.  Can I install now?

---

### Post by saxofoner on 2006-08-17
Should I just try it with the "/mnt/data" on the FAT32 large part?

Can anyone confirm my screenshot as correct?  *I already reduced swap.  What do I do with unallocated space?  Add it to the FAT32 part?

---

### Post by bodhi.zazen on 2006-08-17
So sorry for the confusion.

If you have 2 GB RAM, 4 GB swap if yo follow the "formula". I assume if you bought this much RAM you use it, so swap = 4 GB it is.

Either change back or add the space to the FAT partition.

As to your share partition, what you are setting is the mount point. This is a matter of preference and you can always change it later.

Some advise to mount it in /home. I do not like this because Linux puts user configuration files in /home and there is no need to share them with windows. You can and should back up your /home.

I like /mnt/data as the /mnt directory is the default location for mounted hard drives. You can call it what you like; /mnt/data, /data, or /mnt/share does not matter. As I said, this is not etched in stone and you can always change it later if you prefer an alternate mount point.

Screen shot from 6 hours ago otherwise looks OK.

As far as Windows, eater under the bridge. No worries, no need to start over.

Install away .......

---

### Post by saxofoner on 2006-08-18
Haha!  Thanks to all!  I'm now writing from a computer that booted Linux all by itself.  No CD!  YAY!


You all are the greatest!

---

### Post by Drakkor on 2006-08-18
That's great, saxofoner  !! :D  I installed Dapper about 2 months ago and love it, I still keep XP around just in the odd chance I might need it for something, but I never even use it ! Happy Ubuntuing ! And agreed this forum rocks !! :)

---

### Post by GeekSpeek'r on 2006-08-18
I agree with ' Sean_ ', ~ 1/2 & 1/2 with your physical memory as swap

---

### Post by bodhi.zazen on 2006-08-18
And the journey begins.....

Welcome back from the dark side.

---

### Post by wvslkr on 2006-08-18
Congrats!! Now have fun. If you have problems jump back in here. If some one now's how they will be happy to help.

Peace;)

---

