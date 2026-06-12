---
title: "Newby Problems"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by TehBlanky on 2007-12-25
hello , i am new to the linux world , just downloaded ubuntu OS , it is the best operating system i ever had! (i used a liveCD to explore it). Now , i want to install it , but i want to do in the way so i can't harm my piece of sh*t t windows xp. i tried with partition magic to make an 15  gigabytes ext2 partition , but it seems that   it gives an error when it tries to do that operation ("xmnt2000 not found , aborting operation" or something like that). i tried and with norton partition magic...and its the same error.
i got 3 partitions with the format NTFS , i want to take 15 gb from an partition and make with it an ext2 format

Some info:
I Got Windows XP Professional SP 2
160 Gb Hardware
And i Want To Install Ubuntu 7.10

I Really Need Help , i am tired of crashes , BSOD-s , etc...

---

### Post by LaRoza on 2007-12-25
What are the three partitions for?

You can use the Ubuntu install disk to make and alter the partitions, including resizing the Windows partition.

Ubuntu will want two partitions, one root partition and one swap. You can only have four primary partitions on a hard disk, so you will have to either delete a partition or make an extended partition and create two logical drives (not difficult).

Remember to defrag Windows first, and back up anything critical. If you have the option to create recovery disks, do so. If you do that, you don't need a Recovery Partition (if one of your partitions is a recovery partition, if you made the disks, you could delete it and simplify the process)

---

### Post by TehBlanky on 2007-12-25
> **LaRoza said:**
> What are the three partitions for?

You can use the Ubuntu install disk to make and alter the partitions, including resizing the Windows partition.

Ubuntu will want two partitions, one root partition and one swap. You can only have four primary partitions on a hard disk, so you will have to either delete a partition or make an extended partition and create two logical drives (not difficult).

Remember to defrag Windows first, and back up anything critical. If you have the option to create recovery disks, do so. If you do that, you don't need a Recovery Partition (if one of your partitions is a recovery partition, if you made the disks, you could delete it and simplify the process)

the first partition is where windows resides + some programs
the second is for large programs like adobe photoshop , borland developer studio, dreamweaver etc...
the the final is for downloads and games... i don't i will need this one 

btw , didn't the swap partition was optional ? 

anyway , i will start the defrag. and backup now 
thanks for help :D

---

### Post by LaRoza on 2007-12-25
> **TehBlanky said:**
> the first partition is where windows resides + some programs
the second is for large programs like adobe photoshop , borland developer studio, dreamweaver etc...
the the final is for downloads and games... i don't i will need this one 

btw , didn't the swap partition was optional ? 

anyway , i will start the defrag. and backup now 
thanks for help :D

It is optional, but a very good idea to have. You don't need more than 512 MB.

---

### Post by Lord DarkPat on 2007-12-25
You can first make a FAT32 partition in partition magic and then format it while install. I recommend ReiserFS/EXT3. And BTW, I don't have a swap partition and don't think I'll need it, either

---

### Post by lgambett on 2007-12-25
Just some suggestions...
1) If partition magic does not work try Qtparted. It is free and is included e.g. on the Knoppix Linux Live CD.
2) Prepare EXT3 partitions (not FAT32) to host Linux. ReiserFS is good if you plan to store several thousands of files per directory, as it includes a btree search algorithm for directory search.
3) Create a minimum of three partition for Linux; one for the system (the root partition), one for your /home directory, one for the swap. Yes, the swap is optional, but if you do not have it in case of RAM shortage Linux will drop your processes randomly. Having a separate /home partition is very useful when you want to reinstall the system.

---

### Post by GGLucas on 2007-12-25
Swap partitions are always a good idea to have, even if it rarely uses them, or you'll get problems when your RAM gets full. Anyway, there should be a partition editor on the livecd in System->Administration->Partition Editor, try using that one to create your partitions.
It may also be a good idea to create a separate /home partition for all your configuration files, so when you have to reinstall ubuntu, you won't need to redo all the settings you changed.

---

### Post by bumanie on 2007-12-25
In your situation I would download the gparted live cd and though similar to the partition editor, I believe it is somewhat better because it is specifically designed for altering partitions and has more options than the partition editor. It also handles multiple file system types. 
You are best to have a swap partition and I would suggest you you use ext3 for your ubuntu partitions.

---

### Post by TehBlanky on 2007-12-25
yes , i thinked about that , and i am still thinking about it , make an fat32 partition and then format it to change it to ext2 (but now i am going to change it to ext3 , because it suits better for what i need)
i will try Qtparted and gparted live cd after i will finish with defragmenting.

BTW , i had a problem in the past.
I tried to install debian , on a NTFS partition(windows wasn't located there) , it was on the formating step when , suddenly , it freezed. I restarted  it , and the computer couldn't find any os's , not even the debian installer! 
anyway , i downloaded debian from an site named goodbye-microsoft.com or something like that , i don't believe it was a spyware , since i don't think anyone in this world is so stupid to stop the windows comunity to switch to linux
i just hope that this thing won't happen again , it is...pathetic.

---

### Post by bumanie on 2007-12-25
I have never used qtparted, but have used gparted live cd. You won't have any such problems with it. You will be able to format the drive to ext3prior to installing ubuntu if you wish to. Then during install direct the partition editor to make a /root, /swap, /home partition (or whichever partitions you choose).

---

### Post by The Cog on 2007-12-25
The easiest thing to do would be to use Partition Magic (or whatever you are used to) to clear some free disk space by shrinking an existing partition, and then run the Ubuntu installer. Choose the option to use the free space, and it will then create its own partitions and format them correctly. You need at least 5G of free space I'd say. 

Do not try to make an ext3 partition with PM - many people have unexplained problems with ext3 partitions that PM created.

---

### Post by LaRoza on 2007-12-25
> **The Cog said:**
> The easiest thing to do would be to use Partition Magic (or whatever you are used to) to clear some free disk space by shrinking an existing partition, and then run the Ubuntu installer. Choose the option to use the free space, and it will then create its own partitions and format them correctly. You need at least 5G of free space I'd say. 

Do not try to make an ext3 partition with PM - many people have unexplained problems with ext3 partitions that PM created.

Try the GParted Live CD. (See the link in my sig)

It uses EXT3 fine.

---

### Post by TehBlanky on 2007-12-25
DONE , installed ubuntu 7.10
i made 2 partitions 
an 15 giga /root partition
and an 512 swap partition
all is working perfectly , thanks for all your help , i really apreciate it :)

---

### Post by LaRoza on 2007-12-25
> **TehBlanky said:**
> DONE , installed ubuntu 7.10
i made 2 partitions 
an 15 giga /root partition
and an 512 swap partition
all is working perfectly , thanks for all your help , i really apreciate it :)

Glad to help. (Mark thread as solved)

---

