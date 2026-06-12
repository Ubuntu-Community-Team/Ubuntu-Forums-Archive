---
title: "dual boot partition problem"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Gwok3 on 2006-10-07
I'm completely new to the world of linux, and I decided to try and create a dual boot system on my dell inspiron  E1405
It was running windows xp media center 2005 (basically xp home service pack 2), Centrino duo processor at 1.83 ghz, 1 gig ram, intel 945 graphics.

Anyway, I tried to use the linux system rescue disk, but QTParted wouldn't work - when I tried to resize my NFTS partition, the options were all greyed out.  So, I decided to use gparted - the partioning program included with ubuntu 6.06 LTS.  Hd was thoroughly defragged.  There were already 2 weird extra partitions on the hd, one at the beginnning that was about 30 megs and another at the end that was about 4 gigs and dealt with Dell system rescue, or something like that.  I deleted the dell rescue partition, resized the NFTS partition, created a new ext3 primary partition, then created an extended partition with a 2 gig linux swap partition, and a small FAT32 partition for file sharing between linux and windows.  

Then I hit apply, it ran, and all of a sudden it quit after trying to resize the NFTS, and a small black triangle with an exclamation mark appeared next to the partition.  Somehow this partition only decreased in size by about 4 or 5 gigs, when it was supposed to be about 1/2 it's original size, is still tagged as bootable, and NFTS is replaced by the word unknown. 

I tried to reboot my computer to see what would happen, and I get a little exclamation mark after the dell symbol appears, and then it everything stops.   

I've got no clue what to do.  I did a full system backup using a free trial of Backup my PC to DVD's before I tried the install, but I don't know how to use that.  I don't have an install cd of windows, because dell doesn't send that with laptops for some weird reason.  ](*,) 

I'm open to any ideas...

---

### Post by gn2 on 2006-10-07
Dell, and most other branded PC suppliers don't supply CD's because it's cheaper to just have the re-install data on a separate partition. 
Which you have deleted.

So long as you have a valid Product key, you can install from a (preferably borrowed) windows XP CD.

You'll need to update drivers though, which can be fun.

Good XP help site: [http://www.theeldergeek.com/](http://www.theeldergeek.com/)

Have you tried re-booting with the first back-up disc you created in the drive?
If you are really lucky they will be similar to Symantec Ghost discs and will fix things..
If not you've still got your files backed-up.
Which is always good.

Lesson learned: DualBoot on one drive can be recipe for disaster....

---

### Post by Gwok3 on 2006-10-08
Thanks a lot for the information.

Before I do the reinstallation, is it possible to go ahead and repartition the hard drive the way I wanted to, install windows on one, then install ubuntu and the swap partition on another one, or does windows automatically destroy all partitions or some crazy stuff like that?  Am I just going to have to get another hd to get linux without the live cd?

Thanks again.

---

### Post by bulldog on 2006-10-08
You can use gparted on the live cd to partition your hdd.
Think carefully how you want to devide the space,because resizing afterwards is not without risks.

When you made your decision how to partition,just do it,but let the space you want to give to Ubuntu not partitioned.

Let it as unallocated space,which is easyer to install Ubuntu.

Windows will only install on the partition you give it and does nothing with the rest of your hdd.

---

### Post by CatKiller on 2006-10-08
I'm fairly sure that you can select install partitions for both the Windows and the Ubuntu installs, so you should be fine by making the partitions first. Windows should go on the first partition though, since it gets scared if it's anywhere else.

---

### Post by bulldog on 2006-10-08
> **CatKiller said:**
> I'm fairly sure that you can select install partitions for both the Windows and the Ubuntu installs, so you should be fine by making the partitions first. Windows should go on the first partition though, since it gets scared if it's anywhere else.

Windows need a piece of the first partition to set the bootfiles on so it,s the best way to install windows on the first partition.

Thx for the reminder CatKiller.

---

### Post by bergfly on 2006-10-08
Ok, you say you did a full backup with the Backup DVD software. If it works anything like ghost, you might run into issues if you partition the drive before doing the restore from backup. 

What I would do is restore of widows before doing the repartition, and try again with the resizing of partitions. I am always cautious with these and will do it one step at a time.
Assuming you get windows up and running again, defrag a couple times and then try to resize windows partition only. Don't worry about the other partitions until windows is all neatly resized. Once that works, check to see that you can boot windows. If that is all good, then things are looking up! I might be overly cautious, but I always do only one step at a time.

---

