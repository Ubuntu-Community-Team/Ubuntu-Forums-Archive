---
title: "Partitioning help"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by kimlatraductrice on 2006-10-22
Hello all,

I am getting ready to install Ubuntu for the first time. 

My first roadblock is setting up partitions so I can dual-boot with Windows XP, and I was hoping someone out there could help me. First of all, I read *aysiu*'s very informative article on partitions ([http://www.psychocats.net/ubuntu/partitioning)](http://www.psychocats.net/ubuntu/partitioning)), and more specifically, on FS-Drive. This seems like the option I want to go for. My "problem" is that I already have a partitioned hard drive: three partitions.

A - 41 GB
B - 41 GB
C - 45.9 GB

So how do I do this? **How do I keep XP on one partition, and which partition do I use for Ubuntu, /home, and my shared data?** Some kind of walkthrough would be very appreciated.

Thanks a million (merci mille fois) for your help.
Kim

---

### Post by ReaderRat on 2006-10-22
Would you please run in Terminal
```
sudo fdisk -l
```
(that is a small L, not a 1)
and post the output so we can get a look at your current partitions?

---

### Post by ReaderRat on 2006-10-22
Here is a walkthrough for installing from the LiveCD (with screen shots)....FYI.
[**Installing Ubuntu**](http://www.psychocats.net/ubuntu/installing)
And some more on Partitioning:
[**Partitioning (XP & Ubuntu)**](http://psychocats.net/ubuntu/partitioning)

---

### Post by rccharles on 2006-10-22
> **kimlatraductrice said:**
> I already have a partitioned hard drive: three partitions.

A - 41 GB
B - 41 GB
C - 45.9 GB



What is on these three partitions?

Robert

---

### Post by kimlatraductrice on 2006-10-22
> **ReaderRat said:**
> Would you please run in Terminal
```
sudo fdisk -l
```
(that is a small L, not a 1)
and post the output so we can get a look at your current partitions?

I don't have Ubuntu installed yet. Can I run that off the live CD? 
My current partitions are all in Windows XP.

Thanks.

---

### Post by kimlatraductrice on 2006-10-22
> **rccharles said:**
> What is on these three partitions?

Robert

Windows XP on all three of them. I use one drive for music, one drive for data, and one drive for software.

---

### Post by ReaderRat on 2006-10-22
Do you plan to keep all the music,data, and software that you already have on this disk? If so, how large is the hard disk and is there any space left on it?

---

### Post by kimlatraductrice on 2006-10-22
> **ReaderRat said:**
> Do you plan to keep all the music,data, and software that you already have on this disk? If so, how large is the hard disk and is there any space left on it?

Yes. I might (?) be able to fit all three of these onto one disk (41 GB), or at least two of them onto one disk, if that helps. One of these disks is almost completely empty (44 of 46 GB is empty). Other two disks have 12.7 GB and 29.2 GB of free space.

---

### Post by ReaderRat on 2006-10-22
I am a  bit confused. How many hard disks do you have? And is one of these disks only WinXP stuff? Oh, and Yes, you can run that code in  Terminal from the LiveCD.

---

### Post by kimlatraductrice on 2006-10-22
> **ReaderRat said:**
> I am a  bit confused. How many hard disks do you have? And is one of these disks only WinXP stuff? Oh, and Yes, you can run that code in  Terminal from the LiveCD.

Thanks for your help.

The person who installed my Windows XP partitioned my hard drive into 3 different drives, so I have a C, D and E drive. They are all under Windows XP... only the C: drive (41 GB) has the Windows XP installation files (ie. the WINDOWS folder, Program Files, Documents and Settings, etc.).

I hope that's clearer...

EDIT: What I mean is, XP is only installed on the C:. The other two drives only contain data.

---

### Post by kimlatraductrice on 2006-10-23
Does anyone know how I re-partition my hard drive without losing all my data? I tried fitting everything onto one partition (the one with XP), thinking I could then just repartition the others without touching that one, but I have too much stuff to fit onto only one drive with 46 GB of space.

HELP!

---

### Post by CatKiller on 2006-10-23
Defrag all your partitions first. As many times as you can be bothered with. This will limit the number of file segments that need to be moved when you resize the partition, which makes the operation quicker, and means that less can go wrong. Quite a lot can still go wrong, but you might as well remove a small obstacle.

Then boot up the live cd. If I understand what you've written so far, your C: drive has only 2 Gigs of XP stuff on and can be fairly heavily resized to make space for Ubuntu, and your D: and E: drives are just data that you'd like to be able to keep and access from Ubuntu. (You can only read NTFS by default in Linux, but you can read and write FAT32 - you might want to think about juggling things around enough to get your data partitions as FAT32)

This is all do-able.

You'll also want to find out if the partitions you have already are Primary partitions, or Logical drives in an Extended partition, since you can only have a maximum of four Primary partitions. You'll also want to consider the boot loader - the differences between GRUB and the Windows boot loader. GRUB can boot Windows, and I believe the Windows boot loader can boot Linux with a bit of effort. 

You've a few concepts to research, but it is quite straightforward once you get into it - the Ubuntu installer has a nice graphical tool that you can use to resize your existing partition without losing any data, and then you can just point the installer at the unallocated space and tell it to do its thing.

Good luck.

---

### Post by kimlatraductrice on 2006-10-23
I was hoping to be able to use FSDrive and have the setup as described in this article. [http://www.psychocats.net/ubuntu/partitioning]("Partitioning Windows and Ubuntu")
[IMG]http://www.psychocats.net/ubuntu/images/partitioning5.png[/IMG]

Will the Ubuntu installer be able to "merge" by D and E drives into  one big Ubuntu /home /Shared data partition without losing my data? This is what I don't understand.

I'm sorry I keep asking the same question over and over, but I just can't wait to start installing Ubuntu!!

Muchas gracias to everyone for all their help, this forum is amazing. I can't wait to be the one doing the helping ;)

---

### Post by Mornedhel on 2006-10-23
Re-partitioning a hard drive with data on it is a gamble, have I always heard. As someone just posted, defragging as much as you can will help, but the chances of losing just the vital stuff you didn't want to lose still exist.

You may want to look on the Internet for specialized tools, as I am guessing the Ubuntu installer does not offer extreme security (but is still suitable for simple installs).

---

### Post by kimlatraductrice on 2006-10-23
Ok, so what if I put everything I wanted to keep on my Windows XP partition, and erased everything on the remaining two drives. (so my D and E drives, that I want to merge, were empty.) 
Will the stuff on the XP partition be touched by the installer? Can I leave stuff on there during installation?

---

### Post by Mornedhel on 2006-10-23
As long as you don't explicitely tell him to do something to the WinXP partition, it won't touch it (with the exception of the grub installation so you can choose an OS on boot, but there is no way that will cause any data loss). If you only play with partitions on which there is no data, there are no risks. (I did that and survived.)

---

### Post by user1397 on 2006-10-23
This is what you need to do.  As people have mentioned, defrag your windows paritions as much as possible (twice each at least).  Then backup all your data, to blank dvd's or to another hard drive.  Then you could delete your data and music partitions, using the Gparted program on the ubuntu live cd (it will be under system > administration > Gparted Partiton Editor).  Then using that same program, extend your partition with windows xp on it, so as to have enough space for all the data and music that was stored in the previous two partitions (that you have since deleted).  then you can just start the ubuntu installer (the icon on the desktop), and when you get to the partitioning part, make a new partition in the "unallocated space", with the ext3 file system.  or you could create twp partitions, one for /home and one for /.  also, you must make a swap partition (they say to make it as big as double your amount of ram, but i think if you have a lot of ram, like 1 GB, then you dont even use 128MB of swap ever, at least i dont.) in the next step you choose where you would like the partitions to be allocated to.  thats when you choose the /home partition and / partition.  make sure in this step to not put your windows partition anywhere, or it will be erased.  don't tell it to put /home in your windows partition for example.

---

### Post by kimlatraductrice on 2006-10-23
> **erik1397 said:**
> Then you could delete your data and music partitions, using the Gparted program on the ubuntu live cd (it will be under system > administration > Gparted Partiton Editor).  Then using that same program, extend your partition with windows xp on it, so as to have enough space for all the data and music that was stored in the previous two partitions (that you have since deleted).  then you can just start the ubuntu installer (the icon on the desktop), and when you get to the partitioning part, make a new partition in the "unallocated space", with the ext3 file system.  or you could create twp partitions, one for /home and one for /.  also, you must make a swap partition (they say to make it as big as double your amount of ram, but i think if you have a lot of ram, like 1 GB, then you dont even use 128MB of swap ever, at least i dont.) in the next step you choose where you would like the partitions to be allocated to.  thats when you choose the /home partition and / partition.  make sure in this step to not put your windows partition anywhere, or it will be erased.  don't tell it to put /home in your windows partition for example.

Thank you so much! You answered all of my questions. I'm a bit scared about not putting the windows partition anywhere, but I guess I'll just back up as much as I can and go for it.

THANKS AGAIN!

---

### Post by user1397 on 2006-10-23
> **kimlatraductrice said:**
> Thank you so much! You answered all of my questions. I'm a bit scared about not putting the windows partition anywhere, but I guess I'll just back up as much as I can and go for it.

THANKS AGAIN!no problem, just remember that at the screen that looks like this (this is just an example): [U]
[http://img153.imageshack.us/img153/2556/w2u310xn.png](http://img153.imageshack.us/img153/2556/w2u310xn.png)[/U]
make it look like this: 
**mount** **point:** / **size:** whatever you made it **partition:**  whichever one you created (not the windows one) **reformat**: yes
then another one:
**mount point:** swap **size:** whatever you made it **partition:** whichever one you created (not the windows one)

and you could choose to have a seperate /home partition, but i don't recommended (might run out of space on one).

hey y the way, before you install it, go to a terminal:  applications > accessories > terminal, and type ```
sudo fdisk -l
```thats an L not a number 1.  this command shows you your partitions and what they're called.  most likely your windows partition will be called **hda1** but it could be called something else.  just watch out for the one with filsystem NTFS, that's the windows partition.   write down the name of it, and do not put that name (as in **hda1**) in the **partition** part of the scheme i came up with for u (the picture of the link i gave u).

---

### Post by user1397 on 2006-10-23
also, have you tried this guide: [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing) ?

---

### Post by kimlatraductrice on 2006-10-23
Ok, here is the result of my "sudo fdisk -l":

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5354    43005973+   7  HPFS/NTFS
/dev/hda2            5355       16708    91201005    f  W95 Ext'd (LBA)
/dev/hda5            5355       10708    43005973+   7  HPFS/NTFS
/dev/hda6           10709       16708    48194968+   7  HPFS/NTFS

---

### Post by kimlatraductrice on 2006-10-23
> **erik1397 said:**
> no problem, just remember that at the screen that looks like this (this is just an example): [U]
[http://img153.imageshack.us/img153/2556/w2u310xn.png](http://img153.imageshack.us/img153/2556/w2u310xn.png)[/U]
make it look like this: 
**mount** **point:** / **size:** whatever you made it **partition:**  whichever one you created (not the windows one) **reformat**: yes
then another one:
**mount point:** swap **size:** whatever you made it **partition:** whichever one you created (not the windows one)

and you could choose to have a seperate /home partition, but i don't recommended (might run out of space on one).

hey y the way, before you install it, go to a terminal:  applications > accessories > terminal, and type ```
sudo fdisk -l
```thats an L not a number 1.  this command shows you your partitions and what they're called.  most likely your windows partition will be called **hda1** but it could be called something else.  just watch out for the one with filsystem NTFS, that's the windows partition.   write down the name of it, and do not put that name (as in **hda1**) in the **partition** part of the scheme i came up with for u (the picture of the link i gave u).

Any recommendations for partition sizes? You have been such a big help... thank you so much. Hope I can return the favour one day.

---

### Post by po0f on 2006-10-23
kimlatraductrice,

So how much space have you decided on freeing up?  Are you deleting the two data partitions to install Ubuntu on?  Or just one?

---

### Post by user1397 on 2006-10-24
> **kimlatraductrice said:**
> Ok, here is the result of my "sudo fdisk -l":

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5354    43005973+   7  HPFS/NTFS
/dev/hda2            5355       16708    91201005    f  W95 Ext'd (LBA)
/dev/hda5            5355       10708    43005973+   7  HPFS/NTFS
/dev/hda6           10709       16708    48194968+   7  HPFS/NTFShmm so you got 1 NTFS partitions (hda1, your winsows system), and an extended partition (hda2) which is split into hda5 and hda6 (both NTFS).  so you should backup all your stuff on hda5 and hda6, and then delete hda2, hda5, and hda6.  (using the gparted utility on the live cd.)  then extend your hda1 partition, and make it big enough to hold all your files that were previously on hda5 and hda6 (of course after defragmenting hda1 at least twice).  then use the remaining space for the "/" partition for ubuntu, and if you tell me how much ram you have, i'll tell you a good amount of swap space to have.

---

### Post by kimlatraductrice on 2006-10-25
> **erik1397 said:**
> hmm so you got 1 NTFS partitions (hda1, your winsows system), and an extended partition (hda2) which is split into hda5 and hda6 (both NTFS).  so you should backup all your stuff on hda5 and hda6, and then delete hda2, hda5, and hda6.  (using the gparted utility on the live cd.)  then extend your hda1 partition, and make it big enough to hold all your files that were previously on hda5 and hda6 (of course after defragmenting hda1 at least twice).  then use the remaining space for the "/" partition for ubuntu, and if you tell me how much ram you have, i'll tell you a good amount of swap space to have.

I have 480 MB of RAM. So I should have... 720 MB of swap space?

I think I'd like to have a separate / and /home, like aysiu suggested, so that I can do a clean reinstall and keep all my settings intact.

So I'm going for it this weekend for sure. I'm still a student (I'm finishing my Masters degree) so I need to wait until the weekend to have a bit more spare time. Thanks again for all your help.

---

### Post by kimlatraductrice on 2006-10-25
> **po0f said:**
> kimlatraductrice,

So how much space have you decided on freeing up?  Are you deleting the two data partitions to install Ubuntu on?  Or just one?

Like I was telling erik1397, I'm going to install Ubuntu this weekend, that way I'll be able to take my time and not have to run off to a seminar in the middle of installation. I am probably deleting the two data partitions and just extending the Windows partition a bit. Then I'll use the remaining space for a / partition, a /home partition, and swap. I can't wait for the weekend ;)

---

