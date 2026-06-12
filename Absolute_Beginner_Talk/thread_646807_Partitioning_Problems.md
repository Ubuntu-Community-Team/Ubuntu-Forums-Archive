---
title: "Partitioning Problems"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Gimpy Turtle on 2007-12-21
Hey guys,

I am a total noob at the whole Ubuntu thing, but I installed it previously for the animations like compiz fusion etc. The first time I installed Ubuntu I got to the partitioning screen and I had a slider showing how much i wanted to use and I selected 10gig and it installed perfectly fine, but my old graphics card wouldn't handle the animations so I deleted the Ubuntu partition with Paragon Partition Manager and redisrubuted the free space to my Win XP partition. But recently I got a new graphics card which would handle it, so I tried to install Ubuntu again using the same Live CD, but when i got to the partition screen the Guided one now wants to use all of my hard drive, then I went into the manual one and I says i have no partitions, just 40gigs of free space (my HD is 40Gig)

I was wondering if there was anyway to fix the install so the slider came back up or if the manual partition can show my NTFS partition.:confused:

---

### Post by dstew on 2007-12-21
What version are you trying to install? What are the specs of your computer (processor, clock speed, memory, disk space)?

Boot the Live CD and open a terminal window (Applications -> Accessories -> Terminal). Enter the command **sudo fdisk -l** and post the results here.

---

### Post by Gimpy Turtle on 2007-12-21
> **dstew said:**
> What version are you trying to install? What are the specs of your computer (processor, clock speed, memory, disk space)?

Boot the Live CD and open a terminal window (Applications -> Accessories -> Terminal). Enter the command **sudo fdisk -l** and post the results here.


I'm trying to install Ubuntu version 7.10 (Gusty), My computer specs are as follows:
Processor: Pentium 4, 1.60GHZ
If Memory Equals Ram : 512 MB
Disk Space: 40Gig HD with 30Gig Spare
I Don't know what clock speed is lol :neutral:](*,)


I will post the results of the terminal entry in a minute...

---

### Post by Gimpy Turtle on 2007-12-21
The Results of the Terminal Reading is such:
[B]
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c879c87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3557    28569208+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda3            4865        4865         472+   5  Extended
Partition 3 does not end on cylinder boundary.
[/B]



LOL! Does This Help?

EDIT: This Is What GParted Shows
[http://i156.photobucket.com/albums/t21/ambush_starfish/gparted2.png](http://i156.photobucket.com/albums/t21/ambush_starfish/gparted2.png)

---

### Post by Pumalite on 2007-12-21
Get Gparted Live CD (unless you are running Vista) and format sda3:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
10 GB for '/'
1 GB for /swap
The rest for /home
Then install going Manual and using the partitions made. If Vista; you have to allocate space for Ubuntu with Vista partitioner.
(OTOH, you might have a Partitions Table problem)

---

### Post by Gimpy Turtle on 2007-12-21
Ok i will try that and will post the results of the GParted Theory...

EDIT: It still doesn't work, It shows the free space still but if I try to push new, It asks me to creat a disklabel and it says if i do that it will delete everything off of /dev/sda! HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Save me! I WANT UBUNTU! (while keeping my XP Partition) :)

---

### Post by Gimpy Turtle on 2007-12-22
Does anyone else have something i can do, i'm desperate here lol

---

### Post by dstew on 2007-12-22
Take a screen shot of your Gparted screen and post it to the forum. If you cannot shrink or format the sda3 partition, try to delete it. Do not delete the sda1 partition. If you can delete the sda3 partition, you can then make new partitions out of the unallocated space.

EDIT: OK, I see you already posted the screen shot. Bummer. You might have an invalid partition table for the disk. There are several possible reasons for this. [Here]("http://www.ntfs.com/partition-deleted.htm") is a good post about the partition table. The overall wisdom about this seems to be to use the WIndows disk repair programs to get the partition table freshened up. The [fdisk]("http://support.microsoft.com/kb/255867") program has been recommended. Note this is the Windows fdisk program, not the Linux fdisk program.

Anyway, you will have to work on this using Windows tools, it looks like.

---

