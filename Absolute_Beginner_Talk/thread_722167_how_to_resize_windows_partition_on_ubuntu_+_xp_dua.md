---
title: "how to resize windows partition on ubuntu + xp dual boot system"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by aachen on 2008-03-12
Hello,

I just installed ubuntu yesterday on my windows xp machine for the first time to try it.

I have a 80 GB HDD on which windows xp is 20 GB and the rest 60 GB is ubuntu + swap partition like this:

PartitionA: Win XP 20 GB
PartitionB: Ubuntu 58 GB
PartitionC: Swap 2 GB

But now I want to have it other way around. 
I want Win XP to be 60 GB and Ubuntu 20 GB as I am still new in ubuntu and most of my data is in windows partition. Is this possible ?

thanks
gopesh

---

### Post by bumanie on 2008-03-12
Yes it is possible, however you run a small risk of losing data as altering partitions with file systems on them can go wrong. For instance if there was a brief interruption to your power half way through, good bye file system. After scaring you, I will say I have done this many times and as yet have not destroyed any data. Download gparted live cd and use it, or in ubuntu type>  sudo apt-get install gparted in terminal. Then choose gparted from System --> Administration --> partition editor. It has a gui and can resize, move, format most file systems. Be careful, but as I said I have used it many times without mishap.

---

### Post by jan quark on 2008-03-12
please make a back up of your data before playing with repartitioning

---

### Post by aachen on 2008-03-12
Well I have all data as a backup and havent copied any data yet except ubuntu and windows xp. 
I wanted to allocate more space to windows initially but by mistake the opposite happened.
I hope this will work fine.
Thanks for the answer.

---

### Post by udh on 2008-03-12
> **aachen said:**
> Hello,

I just installed ubuntu yesterday on my windows xp machine for the first time to try it.

I have a 80 GB HDD on which windows xp is 20 GB and the rest 60 GB is ubuntu + swap partition like this:

PartitionA: Win XP 20 GB
PartitionB: Ubuntu 58 GB
PartitionC: Swap 2 GB

But now I want to have it other way around. 
I want Win XP to be 60 GB and Ubuntu 20 GB as I am still new in ubuntu and most of my data is in windows partition. Is this possible ?

thanks
gopesh

Yes, it is possible if you don't have much data on ubuntu system.
I too installed ubuntu 7.10 just 2 days back on my 80Gb hdd. I had winXp and then I installed ubuntu with 10Gb ext3+2Gb swap. I had a corrupt grub booting problem, so I used ubuntu installation CD to reboot and started new installation, in that, there is a partition option where you can alter/modify, delete the partitions. 
Just be cautious while deleting/modifying partition.

If you are able to login to windows, then you can also modify partition. Use windows help/search for 'partition'.

---

### Post by prshah on 2008-03-12
> **bumanie said:**
> 
 or in ubuntu type in terminal. Then choose gparted from System --> Administration --> partition editor. It has a gui and can resize, move, format most file systems. Be careful, but as I said I have used it many times without mishap.

You cannot resize the "/" system using gparted while running in ubuntu. 

The live CD method is correct, only:

1) Boot from live cd
2) Open gparted
3) Right click the swap partition and choose swapoff
4)unmount all mounted partitions
5) ONLY THEN can you move/resize partitions.
6) Dont forget to apply/commit your changes before exiting.

Note that gparted from the live cd crashes often. But it will do so only while you are unmounting the partitions, turning off swap etc. At the crunch time, after committing all changes, it works like a champ!

After it is all done, run ```
sudo update-grub
``` in a terminal.

Data loss is a miniscule partition as bumanie said.

Cheers,
PRShah

---

### Post by aachen on 2008-03-13
I could shrink the linux partition and created another NTFS out of it. But it seems to be primary. I want to make it extended so I can create logical partitions out of it. 
Which option should I choose in Gparted to make it extended?  There are options like ext3, ext2, etc..and I am not sure which one to choose.

---

### Post by prshah on 2008-03-13
> **aachen said:**
> I could shrink the linux partition and created another NTFS out of it. But it seems to be primary. I want to make it extended so I can create logical partitions out of it. 
Which option should I choose in Gparted to make it extended?  There are options like ext3, ext2, etc..and I am not sure which one to choose.

ext2 and ext3 are linux filesystems, NOT extended partitions.

There is an easier way for you. 

From Windows, download and install the Ext2 IFS (Installable file system). This will give you access to your linux partition, as a separate drive letter.

If you still want to do it the hard way:

You can have only one extended partition on your drive. If you already have an extended partition, it will be listed as "Extended" under the File System column of gparted.

If you DONT have an extended partition, you can create one in the free space available after resizing your existing partitions, with the following caveat: In a hard disk, there can only be 4 primary partitions, and if you are creating an extended partition for logical drives, it has to be one of those 4 partitions, eg. you can have 3 primary partitions and 1 extended. So if you do not have an extended partition, and you have 4 primary partitions, then you HAVE to delete one primary partition (I recommend the swap partition) to allow to create a extended partition.

If you DO have an extended partition, you can just resize whatever partition you want, then resize the extended partion (in gparted, right click the partition which says "Extended" under the File System column) and resize it.

You can then create whatever logical drives you want in the extended partition either in XP or in gparted as you wish.

To summarise:

If you already HAVE an extended partition:
1) resize your linux partition
2) resize your extended partition
3) create your logical drives in the free space.

If you DONT have an extended partition:
1) check if you have less than 4 primary partition, if you have exactly 4, delete the swap partition. If you have more than 4, then you already have an extended partition, proceed as above.
2) Resize and move all partitions so that you have a ton of free space at the end
3) Create a new extended partition
4) create the logical drives you want.

If you still are uncomfortable with this (You CAN lose your data in an instant):
1) Use the Ext2/3 IFS driver in Windows (Google for it)
2) Post a screenshot of your gparted screen for exact step-by-step advice.

---

### Post by aachen on 2008-03-14
I solved the problem using Part logic software instead of GParted.

My hard drive was like this before making extended partitions:
Windows Partition : 15 GB primary NTFS
Unallocated space: 45 GB 
Linux Partition: 15 GB  (ext 3) + 2.5 GB swap (extended)

And I wanted to make 45 GB unallocated space as NTFS extended partition and make three 15 GB logical partitions out of it.
I tried first using GParted to convert unallocated space into NTFS extended. But it dint give allow me to make it extended. I dont know why. Generally there are  three options to choose from: Primary, Extended and Logical but Only primary option was highlighted and available. Extended and Logical options were grayed out (unavailable). 

Then I made the live CD of Part logic (just 5 MB) and it allowed me to make 45 GB as extended and make three logical partitions out of it. And this dint take any time at all. 1 minute only. I just clicked made it extended and then resized. Thats it. and then restarted computer. All I had to do was just format those new logical partitions after restarting.

Thanks to all people for replies. 
Gopesh

---

