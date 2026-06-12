---
title: "noob: Installing Ubuntu for dual booting with XP"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by whayong on 2007-06-14
Hi there.  I've been using ubuntu for a few months now on a "linux dedicated machine."  But now, I plan on installing it on my "main computer."  As of now, I will be starting the install from scratch, meaning fresh install of XP, then a fresh installl of Feisty.  I'm doing it this way cause I already messed up the process and have to start over again, haha, good times.

For some reason I have trouble following the dual booting guides.  Maybe I just can't read or I'm slow.

I have to hard drives (A & B).  A will have 3 partitions, and B will have 2.  I want to install both OS's in  HD A and just use HD B for storage.  Is this even a good idea?

THe main question in my post I guess is the part of the install where I have to select and partition my drives.  My thought process tells m I should go to "manual" but then, this is as far as my thought process goes.  I'm dedicating 1 of the 3 partitions to ubuntu (do I format it to NTFS after installing windows? or let it be and take care of it when I install ubuntu?)  Best format for ubuntu?  FAT32? ext2? ext3?  What is the mounting point? I remember getting an option of "/dos" and "/windows."

I also don't seem to understand how I create the swap file.  Say my ubuntu dedicated partition is 40 GB, do I have to resize it to 38 GB and keep the 2 GB for the swap file?  

IS there any noob friendly recommended read that you can point me towards?  

Thanks and I will post back for any other questions I feel I just left out.

---

### Post by LaRoza on 2007-06-14
> **whayong said:**
> 
I have to hard drives (A & B).  A will have 3 partitions, and B will have 2.  I want to install both OS's in  HD A and just use HD B for storage.  Is this even a good idea?

THe main question in my post I guess is the part of the install where I have to select and partition my drives.  My thought process tells m I should go to "manual" but then, this is as far as my thought process goes.  I'm dedicating 1 of the 3 partitions to ubuntu (do I format it to NTFS after installing windows? or let it be and take care of it when I install ubuntu?)  Best format for ubuntu?  FAT32? ext2? ext3?  What is the mounting point? I remember getting an option of "/dos" and "/windows."

I also don't seem to understand how I create the swap file.  Say my ubuntu dedicated partition is 40 GB, do I have to resize it to 38 GB and keep the 2 GB for the swap file?  

IS there any noob friendly recommended read that you can point me towards?  

Thanks and I will post back for any other questions I feel I just left out.

The easiest way would be to:
1. Install XP
2. Install Ubuntu, using the "Resize and install to feed space" option, you will move a slider to show how to shrink the exising partition

Doing it this way is easiest, it will make two partitions, EXT3 and Swap, and install Grub to the MBR. You will be able to boot either Windows or Ubuntu.

You will not need to worry about anything, the defaults are fine.

---

### Post by REDISISTone.nl on 2007-06-14
Hi!

Here is a example what I would do:
> 
Install windows, give this the half of your total HD size...(dont partition the other half)

Next put in your Ubuntu CD and press install....Partition like this (use ext3):
> "/" should get like 2 GiB
"swap" is easy, just format it as "swap" (and that's it)
"/home" should be the remaining space
(you can find good tips on partitioning on the internet, just google it)


So you got the extra HDD for storage...You could do two things...

1. making this a NTFS formatted disk and install NTFS support on ubuntu (and again, google it)
2. making it a FAT32 so both windows and Ubuntu can work with the disk

Hope this is the answer ??

Good Luck

---

### Post by antoz on 2007-06-14
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning) 

A couple of good links

---

### Post by whayong on 2007-06-14
Nice!  Thanks for the help guys.  

Here's what I did last night (before posting).

1.) fresh install of XP
2.) format other partition to NTFS (mistake 1, lol!)
3.) I used the "Resize and install to feed space" option and moved the slider to maximum (is this mistake 2? should I have left some space for swap?)


I noticed a problem when I got an error message on the live CD saying memory space is 100% used or something like that.  This was at about 73% of the install process.  It didn't seem like it continued after this.  I tried rebooting but XP didn't boot anymore, lol.

I will try it again when I get home tonight.  Hopefully all goes well.

---

### Post by whayong on 2007-06-15
Problem solved.  Everything worked out.  Thanks guys!

---

