---
title: "Problems with partitioning when installing Ubuntu"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by dustoashes on 2008-03-03
Hi,

I had previously succesfully installed Ubuntu (older versions) from a LiveCD. After ditching the old version, I tried installing 7.10 from a LiveCD. I am running Windows XP and wanted to do dual boot. I already have partitions.

The problem I encounter is when it gets to partitioning (so far I've only tried automatic resizing, as I don't want to format my partition) and it just freezes there. It alerts me of something (I'm not sure what it is). The DVD-rom seems to act very strangely as it stops and then gets loud, etc. - like the CD has been badly burned. Yet I tried with the minimum burning speed and checking the CD for defects and all is fine. I also tried the old Ubuntu LiveCD and the problem remains.

I've then tried installing Ubuntu from Windows without media, but when I reboot and choose "Install Ubuntu", it says that a file in System32 is missing.

---

### Post by e_james on 2008-03-03
My personal preference is to prepare partitions in advance of the install using Windows or Partition Magic or gparted. Windows software for Windows partitions and Linux software for Linux partitions seems to minimise the minor discrepancies which sometimes arise. Then I normally use the Alternate Install CD with manual partition selection. It's a text only install, no windows, but I find that the questions have more straightforward answers.

---

### Post by dustoashes on 2008-04-06
I'm sorry, but I would need a simpler explanation. What would be the problem with this LiveCD? I'm going to format Windows and perhaps try again to install Ubuntu...

---

### Post by bumanie on 2008-04-06
I think if you are going to install ubuntu into your previous linux partitions, you should choose manual at the partitioning stage. The previous reply is suggesting to use a windows partitioner to partition windows and a linux based partitioner to partition ubuntu. I have always used gparted and found it more than competent at dealing with ntfs and ext 2/3, so personally think using a second partitioner is complicating matters. The other thing being suggested was to use the alternate installation cd which has a text based interface and has good success at installing on systems that don't well from the live cd environment.. If you would like to try it get it from here (tick the check box under the start download message. [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

---

### Post by dustoashes on 2008-04-09
> **bumanie said:**
> I think if you are going to install ubuntu into your previous linux partitions, you should choose manual at the partitioning stage. The previous reply is suggesting to use a windows partitioner to partition windows and a linux based partitioner to partition ubuntu. I have always used gparted and found it more than competent at dealing with ntfs and ext 2/3, so personally think using a second partitioner is complicating matters. The other thing being suggested was to use the alternate installation cd which has a text based interface and has good success at installing on systems that don't well from the live cd environment.. If you would like to try it get it from here (tick the check box under the start download message. [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

So basically I should boot with the LiveCD and prior to installation of Ubuntu create a partition for Ubuntu with GParted?

---

### Post by bumanie on 2008-04-09
If you choose manual at the partitioning stage there is no need to use gparted, as you plan to choose the same partitions you have now. The partitioner, automatically formats the partitions it is going to write to. All you have to do is highlight the partition and choose edit and get the partition to be overwritten by the new installation. I hope that makes sense - it's easy when one has done it a few times, but a bit daunting the first time. Just in case something goes wrong I would back up your home folder first, to be on the safe side. Also, you don't need to make or format swap again, leave it as it is. 
Please post back if you have any queries and someone will try to help. I actually set up my systems with a separate /home partition - it makes things much easier when it comes to reinstalling, because you only have to reinstall to / Your /home partition is safe, as is your data. I would suggest trying the live cd, if it doesn't work then try the alternate cd.

---

### Post by dustoashes on 2008-04-10
Yes, I did that a while ago and ended up messing up a partition with data. 

Is there a way, such as creating partitions prior in Windows and then simply using them for Ubuntu? To what do I have to pay attention (partition type is ext3 or something?)?

---

### Post by e_james on 2008-04-10
I would just like to make some explanatory comments which may be helpful. I don't create or modify partitions on a daily basis but, over the past few years I have used Partion Magic 6 and 8, Windows XP Pro, gparted and the partition manager associated with a few linux distros. Before I start I always consider the consequences of a mistake and backup anything I really don't want to lose. After that, since a mistake can still cost me several additional hours of work, I always proceed slowly and deliberately. No quick decisions. Are you sure you want to do this? ............Yes.

I am writing from memory here and I may not remember all the details correctly.

Partition Magic will create, delete, move and resize FAT32 and NTFS partitions with no problems. It will also handle Linux swap, ext2 and ext3 but someone remarked that it may not do the job exactly right. Partition Magic 8 can't operate on USB external drives.

Windows XP will create, delete and reformat FAT32 and NTFS. It will not create or recognise Linux partitions but it can allocate unformatted space.

The ubuntu live CD comes with gparted ready for use and I have used it many times to prepare drives for both Linux and Windows use. Some resize and move operations are not available. It seems that this is dependent on the hardware drivers available. The gparted live CD seems to have a few more options but I have found that "gparted-livecd-0.3.4-8.iso" won't boot up in at least some of my PCs. "gparted-livecd-0.3.4-2.iso" seems to work fine. It uses a different boot loader. Sometimes, when I use gparted to create FAT32 or NTFS partitions, I end up with "unknown format". I can usually solve this problem at the second or third attempt (maybe by using Windows or Partition Magic). Windows is a bit choosy about its boot partitions so I prefer Partition Magic or Windows for those jobs.

I have only done one install using the ubuntu live CD and I don't recall any significant problems. I have used the alternate CD many times to install to independently prepared partitions without major issues. I do need to check carefully that I have identified the correct partitions. E.g. before I overwrite hda7, I check that it has the expected size and format.

When I have a working Windows or Linux setup, I like to use partimage to make partition backups which I can then use to restore a corrupted or damaged system. It is particularly convenient that I can use an external usb drive to hold the image files. On at least one occasion I have used gparted to copy a partition from one drive to another.

There have been many discussions about the positioning and sizing of partitions for dual boot configurations. This howto probably covers all the likely questions

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by dustoashes on 2008-04-10
I've skimmed through this howto. 

> Bulldog's Partitioning advice
Quote:
Some suggestions for disk partition.
Windows as big as you like.

Create an ext3 10GB for /
Create an extended from the rest off the space.
In the extended,
Create a /home 10GB
Create a swap 1GB
Create a ext3 partition for data if you have space left.
You have a separate /home for some data and a separate /data partition to backup important data.

I think a 10GB / partition is necessary to install programs without running out of space to soon.
Yes it can be 5GB or even less,but I think you shouldn't promote that one.

Is all this necessary? I've created a ext3 partition (10GB) and swap (1GB), like Ubuntu requests. Is there any else I should consider?

---

### Post by R6V2 on 2008-04-10
My idea was, that worked for me, was to format your computer (leave nothing) And then boot from Linux, and set the slider to 50% (Or whatever) And then Ubuntu will only use that 50% and the other part will be unallocated (For windows)

---

### Post by e_james on 2008-04-10
Your partitioning choice depends on your requirements and expectations.

My laptop has a 60GB drive and I have created 9 partitions.
1. Primary - ext3 - 100MB for linux /boot (probably unnecessary)
2. Primary - FAT32 - 400MB for Windows 98 C drive
3. Primary - FAT32 - 10GB Windows XP Pro C drive (only just big enough)
4. Logical - FAT32 - 14GB data drive D )
5. Logical - FAT32 - 14GB data drive F ) could be combined into 1 partition
6. Logical - FAT32 - 10GB data drive G )
7. Logical - swap - 500MB
8. Logical - ext3 - 6GB for linux /
9. Logical - ext3 - 2GB for linux /home

The operating strategy for Windows XP (the main system) is that no data apart from settings is stored on the C drive. If the C drive gets corrupted I can restore it from an image file without overwriting important data.

Since the linux installation (Feisty) is experimental, I can afford to have a small /home partition. There's not much data in it. I upgraded from Edgy to Feisty by a fresh install overwriting only the / partition. My Firefox settings, bookmarks etc. remained undisturbed in /home.

When I have a larger hard drive I use about 15 to 20GB for Windows C drive. No more, to avoid the temptation to store data on this drive, which would complicate the backup strategy. At least 2 Windows data partitions, one for general data storage and one (FAT32 about 30GB) for backup operations and data interchange between Windows and linux.

For linux 10GB for / seems to fit most requirements. This is where application and system software is installed. You have to do a lot of installing to get much above 6GB. For /home I have found that at least 6GB is desirable because the DVD writer will use a temporary image file (4.5GB) in that space.

For data partitions there is no simple upper limit. One of my PCs has 3.3TB of data files spread over 9 data partitions. Currently the largest partition size is 400GB because I backup to spare external drives of that size.

---

