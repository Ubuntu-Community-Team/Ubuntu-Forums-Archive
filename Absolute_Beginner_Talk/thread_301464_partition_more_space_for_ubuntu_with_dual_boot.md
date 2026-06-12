---
title: "partition more space for ubuntu with dual boot"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by manny0 on 2006-11-17
hi i have a dual boot with ubuntu dapper and windows xp home. i originally decided to only do a 4 gig partition just in case i didnt like it. but i like it and i would like to add more space to the linux side. is this possible or do i have to just redo my whole system? ive searched around. but im not really sure on what i should be searching for.

---

### Post by rlozano on 2006-11-17
> **manny0 said:**
> hi i have a dual boot with ubuntu dapper and windows xp home. i originally decided to only do a 4 gig partition just in case i didnt like it. but i like it and i would like to add more space to the linux side. is this possible or do i have to just redo my whole system? ive searched around. but im not really sure on what i should be searching for.

if you are more familiar in doing partition in windows, then i suggest you do it there, and just format it ext3 in ubuntu. bu i think, you will soon outgrow that 4GB unless you separate your personal stuff from your linux system files.

---

### Post by manny0 on 2006-11-17
yea but... how does it work? will it just add more space or what? and what should i use. i never partitioned before.

---

### Post by hal10000 on 2006-11-17
To resize your ubuntu-partition you have to boot from your ubuntu live-CD or from a rescue-CD or use Knoppix. But if you have never partitioned before, you should first let me know something more about your system.
In a xterm type:```
sudo fdisk -l
```
and post the output of the command in the forum. This makes it easier to make any suggestions.

---

### Post by edmund on 2006-11-17
You only want to repartition once, so plan what you need.
I have partitioned my 60Gb drive as follows:
- 15Gb XP
- 30Gb FAT32 shared area
- 15Gb Ubuntu
plus small areas for swap and boot partitions.

The FAT32 area is where I keep all my personal stuff, word/openoffice documents, mp3 files, etc etc.  The FAT32 area can be read and written to by both XP and Ubuntu, so it makes the transition from XP to Ubuntu easier.
Also, XP and Ubuntu can be re-installed without the contents of the FAT32 drive being lost.

The Ubuntu installation/live CD has a partitioning tool which is part of the installation process, or can be activated from a menu in the live CD version.  The tool takes care of a lot of the pain of repartitioning and shows you how the disk is populated before you make changes.  

I'm guessing that most of your disk is XP, with 4GB Ubuntu at the end of the disk.
In my experience, shrinking the XP NTFS partition leaves XP intact, as long as the partition is still bigger than the amount of data on the disk, and the data is all at the start of the partition (defragmenting helps with this).  However, it's best to assume that the contents of the 4Gb partition will be lost. 
So... backup all the data you need from the Ubuntu partition, (and the XP partition just in case), then repartition the disk and install Ubuntu using the Ubuntu CD.

---

### Post by jhenager on 2006-11-17
I can make one suggestion without knowing anything about your system. BACKUP.
Backup any critical data. You always want a safety net when you work with partitions.
See this link for more information on a Linux partition utility, but make sure you understand what you are doing before making these kinds of changes to your system.
[http://www.smartcomputing.com/editorial/article.asp?article=articles/2005/s1602/56s02/56s02.asp&guid=](http://www.smartcomputing.com/editorial/article.asp?article=articles/2005/s1602/56s02/56s02.asp&guid=)
You can also get Gparted, which has similar functionality.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by sinpalabras on 2006-11-17
hi post your partition table.

---

### Post by Orion Cthulhu on 2006-11-18
I want to resize my NTFS partion to add more space to Ubuntu. Am I able to resize both NTFS and ext3? If I resize ext3 (which contains / and /home) will I need to install everything again? Is it better to just create a new ext3 partition? What's the best thing do?

---

### Post by sinpalabras on 2006-11-19
hi  Orion Cthulhu,
                  yes you can rezise ntfs and ext3 partitions. You have to boot windows first, go to control panel and defrag your windows partition (commonly C: ) and then put your ubuntu cd and reboot from there (livecd). Once you see   the ubuntu desktop, start  a terminal and tipe gparted , and the partition manager will come up (it`s a graphical tool), click on the device you want to rezise and you`ll see  all the partitions. Tell me if you understand,and we`ll move on.

---

