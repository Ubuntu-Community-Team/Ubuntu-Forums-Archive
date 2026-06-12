---
title: "Creating FAT32 Partiton from Free Space  ??"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by KB8GT on 2005-07-11
By the time I get my Ubuntu Disk I may have may act togeather on the install.  The disks were placed in the USPS on Sunday 10 July out in California.

I my search and readings the following seems to be the three major steps pertaining to partition  and installation of Ubunto on the drive containing Windows.  The result being a dual-boot system.  Sometimes Step 2 is not addressed.

1.  Resize the single partiion of Windows to a desired size.  This can be done with something like QTParted prior to instalation or resizing can be accomplished using steps in the Ubuntu Install process.  At this point I feel I could do either.

2. Highly Recommended  -- Create a FAT32 Partition for the sharing of files between Linux and Windows.  My search as to 'how to'  comes up empty.  Looking for someone to point in the correct direction.  I have looked at QTParted calling up an empty disk - however "create" is grayed out.  I also have 8GM of empty space on my master  hard drive - "create" is grayed out there also.  Is there some other way (program, procedure)  to create and format the partition in  FAT32 - reducing the free space from Step 1 ?  Can it be done during the Ubuntu Installation  or should it be done before ?  Will the creation put the Windows partition in danger ?

Once Steps 1 and 2 are accomplished - I should have three partitions 1) with NTFS for windows, 2) a nice large one for sharing of files with FAT 32, and 3) Free space for installation of Ubuntu.  When done the final partition  should have sub-partitions with space for Linux proper and its' swap area - using automatic in the install.

At this point I feel great about doing steps 1 and 3.  Yes there are dangers, but I have reinstalled Windows from scratch before.  Should I need to do it again a will pick a partition that is not the whole disk.  That then should bring me back to step 2 and 3: and needing quidence on Step 2.

Thank You
Larry

---

### Post by aysiu on 2005-07-11
[QUOTE=KB8GT]
I have looked at QTParted calling up an empty disk - however "create" is grayed out.[/quote] I've encountered this problem with QTParted as well. I generally like QTParted, but I have to say Mandriva's DiskDrake is top-notch for graphical partitioning. I've never run into any such problems with DiskDrake (even though I don't even use Mandriva--I just use the partitioning tool!).

> Is there some other way (program, procedure)  to create and format the partition in  FAT32 - reducing the free space from Step 1 ?  Can it be done during the Ubuntu Installation  or should it be done before ?  Will the creation put the Windows partition in danger ? Yes, actually, if you already have your partitions laid out, you can ask Ubuntu to format a certain partition as FAT32 and even give it a mount point.

> 
When done the final partition  should have sub-partitions with space for Linux proper and its' swap area - using automatic in the install.  Actually, if you use "automatic," I believe Ubuntu will wipe your entire hard drive clean for automatic partitioning. You should probably--using QTParted or some other tool--set up your own sub-partitions. You should have a swap space. It's up to you whether you want to have a separate /home partition.

---

### Post by KB8GT on 2005-07-11
Sorry gang I did not search the forum deep enough nor did I Google deep enough.  I have found a link as to 'how to' add partitions and format using Windows XP.  Now all I have to do is resize the current 'all disk' partition with QTparted.   Then use the info from the link below to add and format a second partition.  This should leave free space to install Ubuntu when the disk get here.

Wish me luck.  I have already scaned the hard drive, and about to defrag and the then run QTparted to resize Windows.  Next will be the creation of a 32FAT patition.  

Of course I will have to wait till the end of this week or first of next to install Ubuntu.

The link is:  Hope it works.


[http://www.webtechgeek.com/How-to-Partition-a-Hard-Drive-Windows-XP.htm](http://www.webtechgeek.com/How-to-Partition-a-Hard-Drive-Windows-XP.htm)

Thank You 
Larry

PS: I ment automatic on the partition selected for Ubuntu -- no no not on the first partition - that would be Windows

---

