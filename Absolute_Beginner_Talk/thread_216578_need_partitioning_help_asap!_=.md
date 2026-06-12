---
title: "need partitioning help asap! =/"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by oxboy on 2006-07-15
Hi all,

I am currently trying to partition my drive to install ubuntu... I have 15 gigs of unpartitioned space, and i am thinking about doing:

10 gigs for /
4 gigs for /home
1 gig for swap.

Problem is, when i try to create the partitions as ext3, they show up as unknown formats!  

I can't use them to mount anything.  Please help.  Thanks!

---

### Post by oxboy on 2006-07-15
Just an update...

I really messed up... I don't know why but I can't boot into windows anymore.  I think I deleted a partition that I shouldn't have.  Oh well.  Thanks very much anyway.

---

### Post by reacocard on 2006-07-15
I assume you're using the Desktop cd? goto System -> Administration -> GParted and create the partitions there before installing.

---

### Post by ovimunt on 2006-07-15
Well, you can try to fix your Windows first. The MBR might have been overwritten so you just need to fix that.

Put your Windows XP installation CD in and boot from it. Wait 'till it loads all the stuff and then choose to Repair an installation. You'll get to a command line where you have to pick the installation you want to fix. If it didn't detect any Windows installations you're in trouble... If it did detect the installation just press 1 or 2 or whatever is the corresponding number shown next to the installation in the list it gives you. Now just type ***fixmbr*** and press ***y*** when it asks if you're sure about it. Windows should be ok now so type ***exit*** and the computer will reboot.

If however no windows installations were found then you've probably messed up the partitions... :-|

---

### Post by catlett on 2006-07-15
Before you through it all away, you can use the Ubuntu live cd to look at you windows partition. That way you will know if the data is still there or has been erased.
First, do you have the Ubuntu live cd installer? Meani9ng when you installed, did it just list text menus or did it boot into the Ubuntu desktop?
If yes the next step is mounting the windows partition. So first get into the live session and enter this into the terminal ```
sudo fdisk -l
``` Then post the output and I'll give you the commands to mount window's partition.

---

### Post by reacocard on 2006-07-15
or to mount it in GUI, use System -> Administartion -> Disks

---

### Post by oxboy on 2006-07-16
thanks for your responses.  It's been encouraging =).  I am busy at the moment, but I'll post the sudo fdisk as soon as I can.  I was about to give up yesterday but I'll give it another try!

---

### Post by oxboy on 2006-07-16
when running the sudo fdisk -l command, i get this output:


Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2   *           5        2885    23141632+   7  HPFS/NTFS

it looks like the partition is still there.  What really bothers me though, is when trying to install with the live cd, I could not partition my unallocated space into ext3.  It kept giving me unrecognized format.

Also, what is the difference between primary and extended partitions?  Can we used extended partitions for the swap or /home?  Thanks everyone for helping and being patient.

---

### Post by Sef on 2006-07-16
> Also, what is the difference between primary and extended partitions? Can we used extended partitions for the swap or /home? Thanks everyone for helping and being patient.

You can have only 4 primary partitions, so the extended partition is way to be able to make more partitions when needed.

Extended partitions can be used as swap or home or both.

---

### Post by ovimunt on 2006-07-16
Windows partitions the drive like this:

1. You get 2 physical partitions of which the second one is Extended.
2. In the Extended partition you get all your other Logical partitions. 

This means that your drive looks like this:

hd0 - Primary partition - typicaly drive C: (in Windows)

hd1 - Extended partition - you can't actually see this in Windows
[INDENT]hd1.1 - first Logical partition - typically drive D: (in Windows)[/INDENT]
[INDENT]hd1.2 - second Logical partition - tipically drive E: (in Windows)[/INDENT]

And so on...

If, when you install linux, you somehow remove the Extended partitions then ALL your Logical partitions are gone! Maybe not physically - the da
ta is still there until you overwrite it - but from the partition table.

*EDIT:* Now, put in this context, your question whether you can use ***the*** Extended patition for ***swap*** is a bit worrying... It sounds to me like you've removed your Extended partition???

A sensible way to partition your drive for linux would be this:

hd0 - Primary partition - typicaly drive C: (in Windows)

hd1 - Extended partition - you can't actually see this in Windows
[INDENT]hd1.1 - first Logical partition - ext2/3 - linux root - not visible out of the box in Windows[/INDENT]
[INDENT]hd1.2 - second Logical partition - swap - linux swap - not mountable in linux and not visible/moutable in Windows[/INDENT]
[INDENT]hd1.3 - third Logical partition - typically drive D: (in Windows)[/INDENT]
[INDENT]hd1.4 - fourth Logical partition - tipically drive E: (in Windows)[/INDENT]

Of curse, this is not a rule but just a sugestion.

---

### Post by catlett on 2006-07-16
Your output is a little strange in that it lists 1 partition on the drive but that partition is the 2nd partition (hda2... hd= hard drive...a= first drive...2= second partition)

You can have 4 primary partitions on a hard drive, no more. You can have many logical partitions. To do this 1 of your primary partitions becomes an "extended partition" and that partition holds the "logical" partitions.
Just for info... in windows the 4 primaries of the first drive will be C,D,E,F. Most people will only have 1 partition..C and D is there cd drive but there was another partition, the partition would take the letter over the cd drives.
In linux the 4 primaries of the first drive are hda1, hda2, hda3, hda4. If you have logical partitions their numbers start at 5 even if you don't have 4 primaries.

Anyways let's get to the important part. Let's mount the partition and see what happens. Open up a terminal (Applications<Accessories<Terminal) and enter these commands.
```
sudo mkdir /media/windows
```
```
sudo mount /dev/hda2 -t ntfs /media/windows
```If all goes well there will be an icon on your desktop called windows. If not go to Places<Computer<Filesystem<Media and look for the windows folder.
Just double click and see if there are folders in there.
If there are folders, the best thing to do is to copy the data on to some medium before you try restoring the partition.
First try and mount the partition. Post what happens.

---

### Post by oxboy on 2006-07-16
> **ovimunt said:**
> 

*EDIT:* Now, put in this context, your question whether you can use ***the*** Extended patition for ***swap*** is a bit worrying... It sounds to me like you've removed your Extended partition???


I'm not sure what I removed, but I removed something that I needed =).  It was really strange because when I looked at my old partitioning table, I actually had two partitions already, one that had windows and one that had something I didn't know about ( I'm assuming it was the boot stuff that I needed, since it was this tiny (30 mb) partition that I deleted which caused major problems.

I didn't know that we could only have 4 partitions, so when i tried to make  3 more primary partitions for the root, home and swap, I wasn't allowed to.  I thought "hey, I have this small, useless partition, why not delete it?"  As you can see, that was very foolish hehe.

I'm not sure I understand 100% how I should partition again to install ubuntu.  I have approximately 22 gigs in my primary partition right now (Windows).

I have approximately 15 gigs left (unpartitioned).  I should create an extended partition for ubuntu, and inside that partition have 3 logical partitions.  I was thinking 10 gigs for the root, 4 gigs for home, and 1 for swap.  Is this correct?  Thanks.

---

### Post by oxboy on 2006-07-16
> **catlett said:**
> ]If all goes well there will be an icon on your desktop called windows. If not go to Places<Computer<Filesystem<Media and look for the windows folder.
Just double click and see if there are folders in there.
If there are folders, the best thing to do is to copy the data on to some medium before you try restoring the partition.
First try and mount the partition. Post what happens.

I tried to mount windows, but I did not find the folder on the desktop.  When I go to Places<Computer<Filesystem<Media, I find the windows folder, but when I click it, it says permission denied.  Perhaps I entered something incorrectly?  Thanks!

---

### Post by catlett on 2006-07-16
I forgot you mounted the partition as root so you need to be root to access it. Right now you are a user. Luaunch the file brawser this way. Open the terminal and enter ```
gksudo nautilus
``` That will launch it as root and you can view the folder.

As far as partitioning, you can just delete the space, let ubuntu select the unused space and automatically partition it into swap and root. That is perfectly fine.
Or you can do what you said about making an extended with 3 logicals. 
Your swap should be twice your ram i.e. 256mb ram = 512mb swap
root doesn't need to be bigger than 5 gb.
home should be what's left because it holds all your documents, mp3's etc. It will be used like windows uses My Documents

---

### Post by oxboy on 2006-07-17
Thanks for your help.  Thanks for everyones help!  I'll try to install and I'll let you guys know what happens

---

### Post by oxboy on 2006-07-18
I just installed it and everything seems to be working fine.  Thanks for everyone's help and suggestions!

---

### Post by catlett on 2006-07-18
Now that your installed. Take a browse through The Dapper Guide for instructions on getting dvd playback, mp3 support and more. [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide) The only thing to remember is to change your ?etc?apt?sources.list to theirs before you start following the guide. It describes how to do it.

---

