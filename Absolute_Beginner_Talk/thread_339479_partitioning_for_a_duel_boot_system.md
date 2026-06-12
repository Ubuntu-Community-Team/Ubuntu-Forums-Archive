---
title: "partitioning for a duel boot system"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by philmiller on 2007-01-15
I have the live CD and am really interested in giving Ubuntu a serious shot.  I share this computer at home with my wife who will never even think about leaving the comfort of her windows, so I want to create a duel boot system.  I think I have read a whole lot about this but am still nervous even though I have backed up every song, photo and file I could find.  

Given this I have two questions:

1. If I partition my hard drive it will not erase and rewrite the drive, but should contain those windows files to that partition, right.  Like the room analogy I read, I house with many rooms.

2.  I think I read somewhere that there is a way to partition the drive to have a common partion that both windows and linux can read and write to.  Is this possible?

Any and all help is greatly appreciated.  If I need to give more detailed information just let me know what it is I did not include.

Phil

---

### Post by yager on 2007-01-15
Check out the following link.

Aysiu has put together some really great information for new users.  There is a section in getting started about how to lay out your partitioning so that you can have the best of both worlds.

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

---

### Post by housam on 2007-01-16
Welcom to ubuntu.
I prefer to manage the partitioning manually to put every thing under control. You have to keep windows in a separate partition and create another 3 partitions for ubuntu.
Using the the partitioning tool Gparted ( you can download it or use the version on the live CD) you can create the following partitions as an examples:
- 10 - 15G ext3 ( / ) for root
- 1G swap ( useless if more than 1G , you may not use it ever if you have 1G RAM or more.)
- 10-15 Gb is ext3 for /home
After creating the partitions you can follow the tutorial for installation. 

Read [this site ]("http://community.linux.com/howtos/Partition/index.shtml")to know a little about partitions
Fat 32 is readable by both systems but also you can read ext3 partitions through windows using [this driver]("http://www.fs-driver.org/").

---

### Post by louistan3 on 2007-01-16
as the above posted, i thnk most of it is right but i believe the swap partition should depend on how much ram you've got.. coz it might be a waste putting 1gb of swap if you only have 256 mb of ram..

i thnk the best way to count how much swap u need is to multiply ur ram by 1.5.... although i also believe that anything more than 1gb is too much.. :)

---

### Post by Sef on 2007-01-16
> Fat 32 is readable by both systems but also you can read ext3 partitions through windows using this driver.

That is incorrect.  Windows and Linux can both read FAT32, ext2, and ext3 without any additional software.

---

### Post by Canis familiaris on 2007-01-16
You can refer to the following thread, for instructions to dual boot Windows & Ubuntu:
[http://ubuntuforums.org/showthread.php?t=338258]("http://ubuntuforums.org/showthread.php?t=338258")

> **Sef said:**
> That is incorrect.  Windows and Linux can both read FAT32, ext2, and ext3 without any additional software.
From when did Windows support ext2 and ext3?

---

### Post by mikewhatever on 2007-01-16
> =philmiller

1. If I partition my hard drive it will not erase and rewrite the drive, but should contain those windows files to that partition, right.  Like the room analogy I read, I house with many rooms.

Repartitioning the drive means you create new partitions within the free space. If there is no free space, you shrink the existing partition/s to make the space for new ones. Note that all data on a partition will be lost if it is formated. Make sure not to formate your Windows partition, just to keep your wife happy.

> 
2.  I think I read somewhere that there is a way to partition the drive to have a common partion that both windows and linux can read and write to.  Is this possible?

FAT32 is the type you read about. Both Windows and Ubuntu can read/write from/to it. It is used, because Ubuntu can not natively write to NTFS (Windows) partition, and Windows can neither read nor write from/to Ubuntu partition.

After you are done installing, check this page: [http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)

It  explains how to customize GRUB menu to make the PC boot into Windows by default and much more.

---

### Post by bootslap on 2007-01-16
Welcome to the Linux !!

It is fairly common to have apprehensions about a new operating system. However, I believe it is not that difficult. Your live CD installer will guide you through the process. If you only have windows installed on the entire drive, then it is even more simple. The installer will prompt you to resize your HDD and at that point you can choose how much space you want to give to Ubuntu and how much to M$. In the next step, just go with the installer and your Ubuntu will be up and running.. In case you face any problems (which I did initially), just use the alternate CD..

Again ... Welcome to Ubuntu!!

---

### Post by bootslap on 2007-01-16
And no windows does not support ext2 or 3.

---

### Post by old_geekster on 2007-01-16
> **philmiller said:**
> I have the live CD and am really interested in giving Ubuntu a serious shot.  I share this computer at home with my wife who will never even think about leaving the comfort of her windows, so I want to create a duel boot system.  I think I have read a whole lot about this but am still nervous even though I have backed up every song, photo and file I could find.  

Given this I have two questions:

1. If I partition my hard drive it will not erase and rewrite the drive, but should contain those windows files to that partition, right.  Like the room analogy I read, I house with many rooms.

2.  I think I read somewhere that there is a way to partition the drive to have a common partion that both windows and linux can read and write to.  Is this possible?

Any and all help is greatly appreciated.  If I need to give more detailed information just let me know what it is I did not include.

Phil
Phil, this is my advice.

Buy another inexpensive HDD (80GB) and install Ubuntu on it.  Ubuntu will install GRUB on your Windows drive so it will dual-boot.

This will allow your wife to use Windows and you can use Ubuntu, without worrying that one or the other will cause problems.  Since you are new to Linux, if you are like me, I have caused more problems for myself than I care to mention.  If the problem gets too bad, I do a clean install and I am off to the races again.  This will save some strife with the wife.

If your home is like mine, when the wife ain't happy, nobody ain't happy.;)

By the way, I have done it both ways --- dual-boot one drive and dual-boot two drives.  I will work either way.

---

### Post by housam on 2007-01-19
> **Sef said:**
> That is incorrect.  Windows and Linux can both read FAT32, ext2, and ext3 without any additional software.

I can't even see my ubuntu partitions through windows unless I use [this driver]("http://www.fs-driver.org/")

---

