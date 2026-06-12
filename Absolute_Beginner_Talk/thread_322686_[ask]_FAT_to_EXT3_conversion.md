---
title: "[ask] FAT to EXT3 conversion"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by anak_design on 2006-12-20
Me: A recently XP user who decided to use Ubuntu linux on his Toshiba laptop, decided to join this forum for tips and tricks on this amazing, full-of-potential operating system.

anyway...

I've successfully installed Ubuntu on my laptop. Most of the things are working out of the box. I partitioned my drive into 2. 20GB for system, and 40GB for data. Both of them being NTFS. Since I installed Ubuntu, the 20GB system has been converted to .ext3 format. Now that I realized Ubuntu are still having problem with writing access to NTFS disk, I would like to format my "data" drive as EXT3 too. Is there any command I could use? like "format" command on Windows system?

I would need help too on sharing this .ext3 among my system (my main Desktop PC is still windows based). To put it simply, I need to be able to access this drive back and forth between PC and my laptop.

Help please?

---

### Post by meng on 2006-12-20
Here's how I would do it:
identify the partition you wish to re-format. (if not sure, type:
sudo fdisk -l
and you should be able to work out which /dev/??? you are dealing with)

then
sudo mke2fs -j /dev/???

and you have converted to ext3

YOU MUST BACK UP YOUR DATA! your data will disappear with the reformat, and you can then restore it.

---

### Post by Cardmaster91 on 2006-12-20
> **anak_design said:**
> Me: A recently XP user who decided to use Ubuntu linux on his Toshiba laptop, decided to join this forum for tips and tricks on this amazing, full-of-potential operating system.

anyway...

I've successfully installed Ubuntu on my laptop. Most of the things are working out of the box. I partitioned my drive into 2. 20GB for system, and 40GB for data. Both of them being NTFS. Since I installed Ubuntu, the 20GB system has been converted to .ext3 format. Now that I realized Ubuntu are still having problem with writing access to NTFS disk, I would like to format my "data" drive as EXT3 too. Is there any command I could use? like "format" command on Windows system?

I would need help too on sharing this .ext3 among my system (my main Desktop PC is still windows based). To put it simply, I need to be able to access this drive back and forth between PC and my laptop.

Help please?


ok, i dont quite understand. all this "data" that you want reformated, is it in an xp partition? 

but for sharing, your windows can't read the ext3, since windows is fat32. i recommend creating a swap partition, using something like [gparted]("http://gparted.sourceforge.net/"). just resize one of your artitions smaller, and create a new one to about 2gigs (depends on how big of files you wish to exchange). make sure it is fat, so that both windows and ubuntu can read it. then simply restart the computer into watever os u have ur files on, then drag and drop to the swap partition (in windows, it shuld be next to C:, and uibuntu, in nautilus). Then restart into ur other os, and drag and drop from the swap. Done  :/

---

### Post by punx45 on 2006-12-20
i dont mean to nitpick, but you could probably choose a term better than "swap."   since an actual swap partition already exists on the linux side, a more appropriate description of this would be a transfer partition, or something like that.   dont want to cause confusion!

---

### Post by anak_design on 2006-12-20
"Here's how I would do it:
identify the partition you wish to re-format. (if not sure, type:
sudo fdisk -l
and you should be able to work out which /dev/??? you are dealing with)

then
sudo mke2fs -j /dev/???

and you have converted to ext3"

- This doesn't seem to work. I've done this step but my HDD is still in NTFS format. And as I read in another post, Windows can actually handle .ext3 format? since there's a driver for it? I'm not sure. What is the most stable, newbie-friendly, n easy method to make linux and windows friends?

---

### Post by punx45 on 2006-12-21
so you have one physical drive that is partitioned into two parts right?   
one partition is currently EXT3, and the other NTFS, and you want to change the NTFS partition to EXT3, and then have it accessible to your Desktop that still runs windows.

On the laptop you sould be able to go to the System > Administration > Disks menu.   From there you should be able to delete the NTFS partition and create a new EXT3 one.   As always, back up anything you feel you can't live without, because **you will be destroying the current NTFS partition**, and there is always a chance of messing up the entire disk.

Then, read up on SAMBA, which will allow you Microsoft style network shares with the desktop.

---

### Post by NewbieLearnLinux on 2006-12-21
Partition Magic is a Win tool can do that, but maybe the [GParted](http://en.wikipedia.org/wiki/Gparted) or [QtParted](http://en.wikipedia.org/wiki/qtparted) in the [SystemRescueCD](http://en.wikipedia.org/wiki/SystemRescueCD) can also do the job...


EDITED:
Oh man, your topic title is "FAT to EXT3" and your question is "NTFS to EXT3" ... No wonder the guy with 2nd post this thread (meng) tried to convert with that command...

---

### Post by punx45 on 2006-12-21
yep.   GParted should also be on the Ubuntu install CD, and i think, but am not certain, is what System>admin>disks uses.   if not its very similar.

[http://gparted.sourceforge.net/documentation.php]("http://gparted.sourceforge.net/documentation.php")

---

