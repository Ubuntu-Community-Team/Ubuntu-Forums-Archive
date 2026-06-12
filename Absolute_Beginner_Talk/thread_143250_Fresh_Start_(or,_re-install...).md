---
title: "Fresh Start (or, re-install...)"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by asusa83 on 2006-03-12
Hello, 

For the short story, scroll to the bold text.

There was a problem (me) with my original install that I detailed here:
[http://www.ubuntuforums.org/showthread.php?t=143010&page=4](http://www.ubuntuforums.org/showthread.php?t=143010&page=4)

Instead of waiting patiently for a reply, I've just reinstalled Ubuntu.  There was a bit of confusion amongst the partitions and I spent some time following this tutorial from the how-to section:
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

There were some problems with that so I ended up letting the partition manager do the legwork and just reformatted my whole drive.  

NO, this was NOT the drive with XP system/all data thankfully...it's not THAT problem that I'm having \\:D/ 

There are 2 hard drives in my system.  One 80GB with 2 partitions, and another 300GB that now has 1 partition fully dedicated to Ubuntu.  How comfortable it must feel :) 

At some point in the near future (tomorrow morning) **I would like to completely remove Ubuntu from this drive and partition it so that it will still be useful for XP.  THEN re-install Ubuntu (again!) with proper partitions for the OS, a swap directory, and a home directory as mentioned in the tutorial.**

Also, relevant to my reply that I linked to, as I'm reinstalling I had to specify the monitor resolutions I'll be able to use with Ubuntu.  AGAIN, in vain, I pressed enter to try and select my choice and it caused the installation process to resume.  Is 'enter' no longer the key of choice for this part of the installation? Grr...

Well, thanks anyone who can help ;)

---

### Post by encompass on 2006-03-12
Using the windows install CD you should be able to delete all partitions and set up the Windows side of the installation without a hitch.  Then jsut install the Linux side.  I don't see any issues.  But I didn't read all of your post.
:)
Note--- and when you say "useful"  are you meaning that you want an area that both OS's can read?  I would make a fat 32 partition for that.  you know something not too big.  Like 10 or 15 gig.

---

### Post by asusa83 on 2006-03-12
Thanks for the quick reply encompass :D 

Problem is, there is no CD to reinstall windows from...it came with XP pro direct from the retailer.  I've tried going back to a previous restore point, to no avail. 

Also, I'm not sure a partition managing program would work through windows because, since the whole drive is dedicated to Ubuntu, it's invisible in windows :-k 

Maybe someone would know **how to uninstall Ubuntu from outside Windows, reformat the drive so it becomes accessible by Windows (the common space you mentioned, and I know that's discussed around here somewhere), then repartition the remaining space for Ubuntu OS, swap, and home directories before reinstalling.**

Gasps for air after that sentence.

---

### Post by encompass on 2006-03-12
Hey, you know you could jsut reinstall ubuntu and make a small area available for a fat 32 partition that both the windows and linux can share.  That way if you want to transfer data you can do it.  I am not usre if you can make a fat partition with the ubuntu installer.  Bit I know you can do in in linux or in windows.  Windows is the easier one in my eyes.  You use the administration panel and you can look at the disks and format a partition.  I think you may even be able to deleete the old ubuntu partitions with windows too.  From that program.  Goodness can't remember now... been to long :)

---

### Post by oscar on 2006-03-12
Can I clarify what I think your situation is. You have 2 disks, 1 80GB with 2 partitions, one of which has windows XP installed on it, and one 300GB currently with ubuntu taking up the entire disk. You want to re partition the 300GB disk so that windows XP has access to some of it. 

If the above is correct this is what I would do.
Stick the install cd in and reboot.
Select install to hard disk and continue until you get to the partitioning stage.
When you get to this stage select Manually edit partition table.
Delete all partitions on your 300GB disk (be careful not to touch the disk with the windows installation on as it seems that you have no easy way to install windows again). To do this press enter when a partition is selected and then select delete this partition.

Now press enter over free space and select create a new partition. Select the size you want eg 40GB and press enter. Make it a primary partition, you shouldnt have more than 4 partitions on this disk so it should be ok. Make the partition on the beginning of the drive. Make sure that this partition is ext3, mount point and label as / and bootable is on. Now go done setting up partition. This will be the main root partition of your ubuntu installation.

Next select the free space again and create a new partition. Select the size, e.g. 20GB, logical and beginning of drive. Make it ext3 again and mounted as /home. This will be your home partition. Select done setting up partition again.

Now select the free space and create another partition, this time change the use as to swap area and go done setting up the partition. This is your swap partition.

Finally use the rest of the space for your windows accessable partition. Select the free space and create a new partition on it. It should automatically detect the space left on the drive so dont change the partition size.Change the use as to FAT32, this is accessable from windows, you might want to be able to read it from inside ubuntu so set the mount point as /media/storage or something like that..

That should be it select finish partitioning and write changes to disk.

Now continue your installation, both windows and ubuntu should be able to read and write the fat32 partition.

I hope this helps, I booted up my other computer with the install cd in to check what it was like but didnt finish the process.

---

### Post by asusa83 on 2006-03-12
Oscar, 

Yes, it helped \\:D/ Thank you very much :D 

You're the man now dog!
[http://www.yourethemannowdog.com/](http://www.yourethemannowdog.com/)






PS-To anyone who reads this thread subsequently, use the **spacebar** to select the screen resolutions you want to be available.

---

### Post by oscar on 2006-03-12
Glad i could help.

---

