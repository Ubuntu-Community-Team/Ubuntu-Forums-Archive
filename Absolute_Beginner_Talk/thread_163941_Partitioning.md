---
title: "Partitioning"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by GDeadHead on 2006-04-21
Hi.  I'm new to Ubuntu (and Linux) and am trying to install it with a dual-boot with Windows XP.  I am wondering with partitioning if you can change a NFTS partition to a FAT32 without deleting all the files on it.  Also, if that is possible, can Windows run on a FAT32 partition or does it need to be on a NFTS?  I would appreciate any help.

I have a AMD Athalon XP 2800+ 2.09 GHz, 512 mb RAM
A 40Gb hard drive NFTS with Windows on it and a 250Gb hard drive with a 219 Gb NFTS Partition with misc. files on it and a 14 Gb partition that I'm going to put Ubuntu on.

---

### Post by MasonM on 2006-04-21
No, you can't change it from one file system to another without wiping it out. Best to leave your Windows on NTFS.

Why would you want to do this anyway? About the only thing MS did right was getting away from the old FAT file systems.

---

### Post by gondilon on 2006-04-21
windows XP much prefers to run on a nNTFS partition. ALos, I do not believe you can change the typ without deleting all the data on the partition.  WHy do you want to change it to FAT32 anyway?

---

### Post by GDeadHead on 2006-04-21
I read on these forums that NFTS can't be accessed by Ubuntu and FAT32 can be by both Windows and Linux.  I have files on the hard drives which I would like to use with both Ubuntu and Windows.

---

### Post by catlett on 2006-04-21
Windows can run on fat32. But you don't have to switch the format of Windows to put Ubuntu on the drive. The installation will partition out a part of your drive for Ubuntu and will format it to accept Ubuntu. Just put your disk in and run the default install. When it comes to partitioning choose "resize your hard drive and install Ubuntu". (Or something like that it will definately say resize). On the next screen you choose the amount to give Ubuntu. If you have a large hard drive wtite in 10gb, if it is small put in 3gb. Just hit enter to the next screen when it shows you the two partitions it will make. Then just follow the prompts. Usually you can agree to all the defaults and everything is fine. You'll reboot and have a menu with a choice to start up Ubuntu or Windows.
So don't worry about formatting the NTFS. I believe there is a way with the right software and enough space(it will format oart of your drive,move your files and format the rest) but this is tricky and risky. Because reformatting erases data and if the software that moves and formats might have an error and your Windows system is gone. 

P.S. I walked away while posting and didn't see the other posts. There are tools to see your NTFS in Ubuntu. There are also tools to write to NTFS in Ubuntu. You should be able to mount and read the NTFS files without any problems but the writing to NTFS is still risky. There is apost around here that describes the process. Just search for NTFS on the search bar and you'll come across it eventually.

---

### Post by GDeadHead on 2006-04-21
Ok.  Thanks for all the help.  I shall go and put on Ubuntu right now!!!

---

### Post by aysiu on 2006-04-21
[QUOTE=GDeadHead]I read on these forums that NFTS can't be accessed by Ubuntu[/QUOTE] It can be accessed--read--just not written to.

See it? Yes.
Make changes? No.

---

### Post by catlett on 2006-04-21
Just in case anyone is interested [http://www.debian-administration.org/articles/367](http://www.debian-administration.org/articles/367) That isn't the Ubuntu post but it is a Debian post. The app used in both posts is Fuse. So it is possible. Unstable and risky maybe but possible.

---

### Post by RRS on 2006-04-21
I believe your XP operating system needs to remain in NTFS.

The 250gb drive with your data files will be fine in Fat32 which would allow read/write access from either OS but reformatting the partition will erase it.

Can you backup the files on that drive? If so, then no problem.

The partitioning tool in the installation CD can format an ext3 partition for Ubuntu and will automatically create a small swap partition depending on how much RAM you have.

By selecting "manual" from the partitioning menue you will be able to choose the size of the ext3 partition and have it use the rest of the drive to create your Fat32 partition for files and data you want to share between Ubuntu and XP.

You'll find [this guide]("http://users.bigpond.net.au/hermanzone/index.htm") very helpfull.

Hope I've been able to answer some of your questions.

Welcome to Linux. :)

---

### Post by catlett on 2006-04-21
I don't like to bombard new people with alot of technicalities. I try to get to the point and get them started but I want to clear something up. You CAN CONVERT A PARTITION FROM NTFS TO FAT32 WITHOUT DATA LOSS. I have done it multiple times with Partition Magic. You need to have as much free space as the space you are converting because it will move your files away from the formatting. And you can write to NTFS with FUSE, although it is risky.

---

### Post by RRS on 2006-04-21
> **catlett]I don't like to bombard new people with alot of technicalities. I try to get to the point and get them started but I want to clear something up.[/QUOTE]

Point well taken.

> You CAN CONVERT A PARTITION FROM NTFS TO FAT32 WITHOUT DATA LOSS. I have done it multiple times with Partition Magic. You need to have as much free space as the space you are converting because it will move your files away from the formatting. 

Didn't know that, thanks for tip. Unfortunately it doesn't appear that GDeadHead has that option said:**
> .......a 250Gb hard drive with a 219 Gb NFTS Partition with misc. files on it........

BTW, I wish a had found my way to this forum before my first installation rather then a couple weeks later, I'd be alot further up the learning curve.

Edit: gotta work on my typing too :)

---

### Post by GDeadHead on 2006-04-22
Backing up with CD's is deffinently out of the question and I have nothing else to back up with.  I have around 40 GB of data.  I think RRS has misunderstood the amount of space I have (or I just typed i out wrong).  I have a 40GB approx. data on a 219GB partition, so there is enough free space for the Partition Magic Tool to work.

BTW, I'm on Ubuntu right now for the first time.  Just got it installed!!! :)

---

### Post by GDeadHead on 2006-04-22
Ok....  Now I think I just messed up Ubuntu badly....   It won't start properly...  I was reading the guide that RRS put a link to and I was reading about accessing the other hard drive partitions when I realized they wernt even there.  I kept on reading and edited the fstab file like the guide said so I would have permision to edit stuff (I think I messed up something there).  Then I continued on reading and it got to a part about detecting the hard drives.  It had this line to force a filesystem:

           sudo touch /forcefsck

I also did that.  Now whenever I try to go onto Ubuntu, It does the filesystem check with the ===== going across the screen fine, but after that, it has some stuff that fails.... I am pretty sure it had to do with editing the fstab document.  but then I can log on but all I have is a command line and I don't know how to do anything....  I would greatly appreciate help with this.

Oh-yay.  There is one more thing, but it is not related to the problem above.  When I partitioned the hard drive when installing Ubuntu, it somehow had made The 219GB partition become 36GB!!!!  Not good!

---

### Post by gondilon on 2006-04-22
if you go to this web page :[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
You can get a program that will allow you to read and write your linux partition from windows. Then you can save files from windows to your use linux partition and be able to use them in liux.

---

### Post by GDeadHead on 2006-04-22
I can read my Ubuntu oartition with that program but I can't wirte with it...

---

### Post by cjm5229 on 2006-04-22
The safest way to move files back and forth from Windows to Linux would probably be to make about a 15 Gig. Partition in fat32 then just copy your files into that. I have an old 13 gig. HDD I put in just for that purpose and it works quite well. That way you aren't going to mess up either file system.

---

### Post by GDeadHead on 2006-04-22
I have to change the fstab back in Windows because I can't get on to Linux.  It wont start up.

---

### Post by tuxcantfly on 2006-04-22
actually, instead of explore2fs, use ext2ifs. It's an actual filesystem driver, not just an application like explore2fs

get it at: [http://fs-driver.org/](http://fs-driver.org/)

---

### Post by RRS on 2006-04-22
Since I misread your original post on the amount of space you had available (apologies BTW) I would like to clarify:
> ..........but then I can log on but all I have is a command line and I don't know how to do anything............ 

Are you saying that Ubuntu does finally start and ask for your loggin and password but remains in terminal with no GUI?

IF that's the case then you should be able to:
```
sudo nano /etc/fstab
```

Again, IF this works, then for the moment I would simply delete the lines pertaining to your windows and fat32 partitions to return the fstab file to it's original configuration.
 
I can't remember the command to list your partitions, I'll go check my notes.

If you aren't actually booting into terminal let me know and one of us may still be able to help.

---

### Post by tuxcantfly on 2006-04-22
also, what does your /etc/fstab say? is / is it under the mountpoint section? also, check /etc/fstab~ it's a backup file, unless you've changed fstab twice you should be able to restore it and fix your fstab

---

### Post by tuxcantfly on 2006-04-22
also, the command to list your partitions is

dir /dev/hd*
dir /dev/sd*

use the 1st one if you're using old (ata) drives, use the 2nd one if you're using new (sata) drives

you should get something like

/dev/hda  /dev/hda1  /dev/hda2  /dev/hdb  /dev/hdb1  /dev/hdc

the ones with numbers on them are the partitions; make sure they're in /etc/fstab or you'll be unable to use them

---

### Post by GDeadHead on 2006-04-22
I had only read privalages.  I just decided to re-install Ubuntu and its now installed and working fine again!  I am not going to mess it up this time.

I made another partition on my drive (FAT32) big enough for all my files so I now just have to copy them.

Thanks for all the help you guys have given me!  I shall enjoy being part of the Ubuntu community!

---

