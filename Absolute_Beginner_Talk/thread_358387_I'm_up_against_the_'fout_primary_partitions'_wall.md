---
title: "I'm up against the 'fout primary partitions' wall"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-02-10
Hi

I am trying to set up ubuntu on the same machine as winXP home in a way that allows me to share thunderbird email. (i.e. so I can read / delete messages from either OS) 

The advice I recieved via this forum (thanks all) was to create a separate FAT32 partition onto which I could put my thunderbird profile (and lots else) that I wanted to share.


So after a bit of Gparted'ing, I have ended up with (approx. on an 80 Gb drive)

 1: FAT 16, 58Mb: Don't know what's this is for, maybe a DELL thing
2: ext3 , 7 Gb where ubuntu is installed
 3: linux swap , 1.2 GB
 4: 20 odd GB unallocated
 5: 45 odd Gb of NTFS (windows etc.)

I then tried to create a FAT32 partition on the 20 GB between the linux swap partition and the NTFS partition. I got a message along the lines of 'you can only have four primary partitions. Create an extended partition'

Well, I don't know how to do that so I hope you can help.

TIA

---

### Post by nickoli_02 on 2007-02-10
Try formatting it as a logical drive? Worth a shot...

---

### Post by mikewhatever on 2007-02-10
Creating an extending partition is an easy job, once you find the option.
> Then, Ubuntu will show you your partition table--what partitions you have and what filesystems they use. If you right-click on a partition, you can choose to resize it or delete it. In any empty space you create, you can right-click on the empty space and create a new partition. The partitioning program the Ubuntu installer invokes is called GParted. You can see how it works at the GParted homepage.
This is a quote from the [installation guide]("http://psychocats.net/ubuntu/installing"). I suppose, right clicking on the empty space will give you the option, but not quite sure, because I used a different kind of installer.

---

### Post by ubername on 2007-02-11
> **mikewhatever said:**
> Creating an extending partition is an easy job, once you find the option.

This is a quote from the [installation guide]("http://psychocats.net/ubuntu/installing"). I suppose, right clicking on the empty space will give you the option, but not quite sure, because I used a different kind of installer.

Hi

Thanks, thats what I tried to do but when I selected 'new' it said ( in effect) 'you can only have four primary partitions.'

However, all is now well as I deleted my linux swap partition, combined the empty space and then created a new extended partition. Into this I put a logical linux swap, and a logical FAT32. All seems to be well for now!

Still working on the Thunderbord profile thing though!

---

### Post by ubername on 2007-02-12
> **ubername said:**
> Hi

Thanks, thats what I tried to do but when I selected 'new' it said ( in effect) 'you can only have four primary partitions.'

However, all is now well as I deleted my linux swap partition, combined the empty space and then created a new extended partition. Into this I put a logical linux swap, and a logical FAT32. All seems to be well for now!

Still working on the Thunderbird profile thing though!

All sorted now! Had to edit profiles.ini in FF and TB, both Linux and windows, but now all is running well. Thanks all.

---

