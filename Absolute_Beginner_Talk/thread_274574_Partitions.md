---
title: "Partitions"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by rakesh343 on 2006-10-10
I am trying to install UBUNTU 6.06 LTS "DAPPER DRAKE" from a CD on my laptop which already has WINDOWS XP as an OS. I would like to keep the dual boot. The thing is I can not partition the hard disk. If I look at the partition table, it shows the following:
1. A FAT16 segment
2. A NTFS segment
3. An unallocated space
4. A FAT32 segment
5. An unallocated space
As you can see, there are already three primary partitions, and I can not create the other two, one "/" and another "swap". The two unallocated spaces are not contiguous and are sepated by the FAT32 placed between the two. This is probably creating problems.

Any suggestions?

---

### Post by jorn on 2006-10-10
You can download and burn the gParted live-cd to patition your drive and get a better overview.

---

### Post by Jussi Kukkonen on 2006-10-10
You might have run into the primary partition limitation of the Intel platform: there can only be four of those. If this is the case you need to start playing with extended and logical partitions. This is not that difficult and gparted or the Ubuntu installer should be able to that. 

More info here:
[http://tldp.org/HOWTO/Partition/index.html](http://tldp.org/HOWTO/Partition/index.html)

---

### Post by hyper_ch on 2006-10-10
so if you are still on windows I recommend to have a look at partition magic. I used that to deal with all partition issues on windows (before I used linux).
[It even did let me resize me the linux root partition "/" without breaking anything... I resized it from 120 GB to 30 GB and created then with the rest a "/home" partition]

---

### Post by rakesh343 on 2006-10-12
Let me just show you how my partitions look like. When I tried partitioning manually, my hard disk shows this structure:

FAT16     NTFS     unallocated     FAT32     unallocated
 

The problem with this is the following:

1. There are already three primary partions: FAT 16, NTFS, and FAT 32. I can create only one primary partition.

2. The two unallocated free spaces are not contiguous.

I cannot delete the third Partition "unallocated" as I right click on that there is no option shown to delete it. I couldnot shrink it to zero either. I cannot delete FAT16 as it contains perhaps WINDOWS program files. FAT32 is also showing some used space though I wonder what it could possibly be. NTFS is needed to run WINDOWS.

Is there any way to know what files are there on FAT32? So That I can delete it if found unnecessary.

---

### Post by jorn on 2006-10-12
Boot from live-cd.
Paste into terminal:
>  sudo fdisk -l
Recognize the fat partition, and mount it:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)
Hope it works.

---

### Post by man-man on 2006-10-12
Sorry if this hijacks the topic but I have a partition question about XP - does Windows need a separate partition from your files to install the OS into?

and if it doesnt *need *to have one, are their advantages to having one anyway? (or disadvantages)

---

### Post by jorn on 2006-10-12
I'm not sure I understand.
You can't install several OS's on the same patition.
A filesystem is something you mount on a partition to access it and handle the content of it.
You must create a new partition if you want to install a new OS regardless of you install linux or mswndows.
If your question is not anwered, please try another wording.

---

### Post by man-man on 2006-10-12
I was fairly sure of the answer to start with, but what i meant was, if you have a computer running windows, does windows itself need to be in a separate partition to your main partition where you put all your files..

damn, thats essentially the same wording

is it 
||  Windows  ||  Files  ||
or can Windows be in one NTFS partition with a bunch of other stuff?

I'm wondering because I'm looking to dual boot and I can see a use for 6 different partitions, if theres a max. of 4 then I guess I need to use extended/logical partitions (never heard the term until earlier in this topic ;) )

---

### Post by bulldog on 2006-10-12
Windows can be installed on partition let's say a.
You can install other programs on a too.

Thus not an apart partition is needed for your windows.
Make it larger and you can put your other data along side it.

Your drive can only have four primary partitions.
This are partitions where you can boot an OS from.

When you want more partitions,you create an extended partition,where you can not put any data on,and within the extended partition you can create logical volumes.

You actually will not notice the difference,but in most cases you cant boot an OS from a logical partition.

---

### Post by man-man on 2006-10-12
Ok, i think that would work out for me, so if i'm limited to 4..
I guess it would go 1 for Windows, 1 for Ubuntu, swap partition for Ubuntu then an extended partition split into NTFS, Ext3 and FAT32 logical volumes?

wow... i just had one of those moments when a little lightbulb turns on inside your head :mrgreen: thanks

---

### Post by ReaderRat on 2006-10-12
[QUOTE=rakesh343;1599522]I am trying to install UBUNTU 6.06 LTS "DAPPER DRAKE" from a CD on my laptop which already has WINDOWS XP as an OS. I would like to keep the dual boot. The thing is I can not partition the hard disk. If I look at the partition table, it shows the following:
1. A FAT16 segment
2. A NTFS segment
3. An unallocated space
4. A FAT32 segment
5. An unallocated space
As you can see, there are already three primary partitions, and I can not create the other two, one "/" and another "swap". The two unallocated spaces are not contiguous and are sepated by the FAT32 placed between the two. This is probably creating problems.

Any suggestions?[/QUOTE 

[Partitioning Windows & Linux](http://psychocats.net/ubuntu/partitioning)
Several partitioning tools can be found on the [color=blue]Free[/color] [System Rescue CD](http://www.sysresccd.org/Main_Page)....**Read The Directions**

---

### Post by rakesh343 on 2006-10-14
Let me just put my questions differently as I am unable to understand all that is suggested.
1. Can I Know what files are there on my FAT16? It shows 7 MB of used space out of a total of 47 MB. If there is nothing, can I delete the Partition?
2. Same question for FAT32. It shows 3GB of used space out of about 15GB. Can I delete this partition too?
3. How can I make the two separated unallocated partitions contiguous? That is, Can I move partitions, change the order in which they appear?

---

### Post by jorn on 2006-10-14
If you want to known what files there are on your fat16 or fat32 you must mount the partitions and read their content. 
Yes, you can delete the partitions. gParted or other apps.
I dont know if you can move or change the order of partitions, havn't tried it myself. You might try it.

---

