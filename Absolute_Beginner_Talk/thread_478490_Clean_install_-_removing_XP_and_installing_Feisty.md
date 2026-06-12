---
title: "Clean install - removing XP and installing Feisty"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by nothinghead on 2007-06-19
I've backed up all of my important files to an external HD and now I want to completely delete XP and give my computer over to Ubuntu.

Right now, my main HD has three partitions, one of them is my "XP Recovery Partition" and one is a vestige of a past Ubuntu install that Norton Partition Magic can't seem to delete or merge with my main C: drive.

If I get to a DOS command prompt and format my C drive, will that wipe out the partitions as well before I boot up my CD and install Ubuntu?

How can I best go about this?  My XP install is buggy and I want to wipe it clean.  I have a "Lite" version of XP on a disk I'll install if things go wrong with my Ubuntu install, but either way, I want XP as I have it, and the extra partitions on my main drive gone.  

Please advise.  Thanks!

---

### Post by LaRoza on 2007-06-19
Wiping your entire drive is easy, you select the option that says something like "Wipe and Use Entire drive". This will delete EVERYTHING, and create two partitions, one in EXT3, that's where Ubuntu is, and one Swap.

-edit I can not tell if you want to keep XP or not, the above instructions will wipe everything, all the partitions.

---

### Post by moredhel on 2007-06-19
As LaRoza says above, just choose the easy option. Good luck, I just wiped windows from my hdd fully as well ;)

---

### Post by rickycodie on 2007-06-19
i would caution against removing windows completely as it is the main os in use. but if you want to go ahead. 
one of the websites i use for school detects the os you are useing and if it is not windows, sorry.

but you can still install windows after ubuntu, so if you incounter a need after you can put it on, it's just a little more complicated. but still not hard.

---

### Post by hyper_ch on 2007-06-19
Well, I wouldn't use the auto partitioner ("Wipe and use entire drive").

I'd advice to make leave that recovery partition as it is. You never know when you need it again....

Then for Ubuntu (if you have at least 100 GB) I'd go for this:

Swap Partition --> double of your ram size / not more than 2 GB --> Type is "SWAP"
Root Partition --> 10 BG (maybe more if you have pleeeeenty of diskspace) --> Type is "EXT3" and mount point is "/"
Home Partition --> The rest of the drive. That is where you personal data files will be stored --> Type also "EXT3" and mount point is "/home"

They can either be primary or extended partitions... that doesn't matter. You can have 4 primary ones and with that setup you will have those four primary partitions....

Use the manual partitioning option. That is not really that difficult... all you need to know is how much diskspace to assign to what partition and what the filesystem and mounting point shall be :)

---

### Post by p_quarles on 2007-06-19
> i would caution against removing windows completely as it is the main os in use. but if you want to go ahead. 
one of the websites i use for school detects the os you are useing and if it is not windows, sorry.

but you can still install windows after ubuntu, so if you incounter a need after you can put it on, it's just a little more complicated. but still not hard.

I seriously doubt that it's filtering your OS. Any web designer who thought of that should be hung by his toes. The site probably requires MS Internet Explorer, which you can run under Linux (using Wine). You can also use Opera and then set it to pretend it's Explorer. No reason to keep Windows unless you have an application that won't run on Linux.

>  I'd advice to make leave that recovery partition as it is. You never know when you need it again....

Most systems that come with a recovery partition also come with a tool for making a set of backup disks based on that partition. You should definitely make those disks before installing Ubuntu.

---

