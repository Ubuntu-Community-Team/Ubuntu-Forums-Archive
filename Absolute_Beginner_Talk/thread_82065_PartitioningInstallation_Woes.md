---
title: "Partitioning/Installation Woes"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by Schmoopie on 2005-10-25
Newbie alert!  Installation/ partition question ahead.  Newbie alert!  

My PC setup is as follows:
-- Currently running Windows XP Tablet 
-- 40 GB total hard drive space, with a 15 GB partition with 5.83 GB free, a 21.5 GB partition with 7.17 GB free, and a (I think) 356 Mb partition (I assume the 356 Mb partition is something the university did, as I never knew it existed until I tried installing Ubuntu).  I know the numbers don’t add up, but that’s what the computer is telling me.  
-- Intel Pentium M processor 1500MHz
-- 1.49 GHz, 760 Mb of RAM

I'm trying to install Ubuntu Linux on my laptop, and having some trouble with the partitioning of the drive.  Before we go too much farther, I must admit that the laptop is leased from the university I attend, and I have had problems with some hidden programs/objects that are placed on the laptop to prevent certain changes.  Although a lease, the laptop is still essentially mine to do with as I please.  I would like to keep Windows installed on the system, as I need it to run some programs for my classes.  The university has the C:\ drive setup as the main drive to run programs, and windows from; with the D:\ drive used as document/file storage.  

Anyway, when running the installation, everything works fine up until partitioning the drive.  When I use the installer's partitioning wizard, it won't let me change the size of the existing partition(s) to free up space.  I accidentally tried, and somehow messed it up, changing the size of the C: drive.  This resulted in none of my programs in windows running properly, and me having to go to the university’s tech support to have the C:\ drive re-imaged.  Lucky for me, I didn’t have anything important stored on the C:\ drive at the time of re-imaging.  

This leaves me with one location to install Ubuntu to, the D:\ drive.  However, when trying to use the Ubuntu installer’s partitioning program to enter a smaller size for the D:\ partition, it appears as if the changes were not accepted, and the partition size remains the same.  What might this be?  No matter how many times I have tried it, I cannot change to size of the partition to free up some space.  I really need/want to have the files on this drive to work in at least Windows, if not in Ubuntu as well.  

As a secondary question, I am curious exactly how much space to allocate to install Ubuntu on.  I have version 5.04 that I copied form a friend, and will be getting version 5.10 in the mail soon.  I have heard that I will need at least 1.08 GB to run Ubuntu without being able to create and save new files and documents within Ubuntu.  I can make more room than this if needed (obviously I would like to have the space to save files under Ubuntu).  However, I was curious if it is possible to set up Ubuntu and Windows so that they both can read and write to, say the D:\ partition.  

So … how much space should I free up, and is it possible to have Ubuntu and Windows read and write to the same partition?  

My main is concern is messing something up that cannot be fixed or recovered.  I recently came to the realization that Ubuntu’s partitioner erases the partition it is changing the size of.  This being said, is there a way to partition the drive (preferably free) without erasing the data on the drive?  I can back everything up and then put it back on the drive, but I would prefer to be lazy and just “squish” the partition, i.e. change the size but keep the data, rather than erase it in the process.  

I love using the Live CD, and would really appreciate any help that is out there.  Sometimes there seems to be so much information to go through, I never know where to start.  Thanks in advance for the help!

Kuecker a.k.a. Schmoopie

---

### Post by darrenrxm on 2005-10-25
I used partition magic 8 to resize my hard drive. It works like a charm. Why don't you ask your university&#8217;s tech support to resize a partition for you? They would have the software necessary to do it. And it wouldn't take very long to do. As a bonus you would have a very small chance of any loss of information. Those tech guys really know what they are doing.

But I don't understand why you don't backup your d: drive to dvd. And then delete it with the ubuntu partitioner and reformat it with ext3 filesystem. Then use the rest as a fat32 partition to share between windows and ubuntu.

---

### Post by atoponce on 2005-10-25
> **Schmoopie]Newbie alert!  Installation/ partition question ahead.  Newbie alert!  

My PC setup is as follows:
-- Currently running Windows XP Tablet 
-- 40 GB total hard drive space, with a 15 GB partition with 5.83 GB free, a 21.5 GB partition with 7.17 GB free, and a (I think) 356 Mb partition (I assume the 356 Mb partition is something the university did, as I never knew it existed until I tried installing Ubuntu).  I know the numbers don&#8217 said:**
>  
The numbers add up.  10% of the drive is reserved to formatting and the filesystem.  15GB+21.5GB+356MB=~37GB, which means ~3GB (10%) is reserved for formatting and the filesystem.

[quote=Schmoopie]Anyway, when running the installation, everything works fine up until partitioning the drive.  When I use the installer's partitioning wizard, it won't let me change the size of the existing partition(s) to free up space. 
You need to defragment the partitions and move all the data to the front of the drive.  I'll bet that's your problem.  Windows does not defrag the data by default.  You'll have to run the builtin defragger.

> **Schmoopie]As a secondary question, I am curious exactly how much space to allocate to install Ubuntu on. [/quote] 
I personally would reccomend nothing less than 5GB, but that's just me.

[quote=Schmoopie]However, I was curious if it is possible to set up Ubuntu and Windows so that they both can read and write to, say the D:\ partition.... So &#8230 said:**
>  
You will not be able to write to the Windows partition using Linux if the Windows partition is formatted as NTFS.  Although it is capable in the kernel to do so, it is unsupported and can cause data corruption and/or drive failure.  As you can guess, it is turned off by default and you will need the kernel sources to turn it on.  Also, you would have to recompile the kernel.

[quote=Schmoopie]My main is concern is messing something up that cannot be fixed or recovered.  I recently came to the realization that Ubuntu&#8217;s partitioner erases the partition it is changing the size of.  This being said, is there a way to partition the drive (preferably free) without erasing the data on the drive? 
The patition utility in Unbunt is great.  You don't have to erase the drive in order to partition it.  Follow the on screen prompts.  You shouldn't have any troubles.

---

### Post by Schmoopie on 2005-10-27
> I used partition magic 8 to resize my hard drive. It works like a charm. Why don't you ask your university’s tech support to resize a partition for you? They would have the software necessary to do it. And it wouldn't take very long to do. As a bonus you would have a very small chance of any loss of information. Those tech guys really know what they are doing.

My University tech. support are really Nazi's when you do something you know will work, but they don't understand.  I have a few friends who asked for thier help with partitions, or tech. support found out they had Linux on the laptop, and tech. support freaked out.  Since I posted last, I did get a copy of Partition Magic 7 from a friend, and right now I'm working on backing up my major files, and defragging the drives.  

> But I don't understand why you don't backup your d: drive to dvd. And then delete it with the ubuntu partitioner and reformat it with ext3 filesystem. Then use the rest as a fat32 partition to share between windows and ubuntu.

My laptop only has a CD burner.  Currently I am utilizing the University's offered network storage, some CD's I've made, and a reliable online storage/backup service to backup the files.  I have decided, that when ready, I will make the D:\ drive a FAT32 so that both Ubuntu and Windows will be able to read and write to both.  I had hoped there was a way to do it without having to wipe the drive, but I guess it is good to have everything backed up anyway.

Kuecker a.k.a. Schmoopie

---

### Post by Schmoopie on 2005-10-27
> 
[QUOTE]Quote:
Originally Posted by Schmoopie
My main is concern is messing something up that cannot be fixed or recovered. I recently came to the realization that Ubuntu’s partitioner erases the partition it is changing the size of. This being said, is there a way to partition the drive (preferably free) without erasing the data on the drive?

The patition utility in Unbunt is great. You don't have to erase the drive in order to partition it. Follow the on screen prompts. You shouldn't have any troubles.[/QUOTE]

I've heard both ideas - that Ubuntu will erase everything when partitioning, and that Ubuntu will NOT erase everything wehn partitioning.  Which is true?

Kuecker a.k.a. Schmoopie

---

### Post by LHZ on 2005-10-28
> 
I've heard both ideas - that Ubuntu will erase everything when partitioning, and that Ubuntu will NOT erase everything wehn partitioning. Which is true?

It depends. The easiest way to repartition a drive in to nuke everything on it, and start again. In this case, you delete an existing partition, and make new partitions in the free space. Needless to say, this means you lose your data.

Many partition programs support 'shrinking' and 'expanding' of partitions, in which case a chunk of empty space is taken from an existing partition and made into a new one. In this case, the data on the old partition will be intact (...if everything goes correctly). This only works if the data on a partition is more or less 'in the same space', so the partition program can cut out a nice chunk of emtpy space. That's why you should defragment three times before attempting this. 

If you have the luxury of back-up, I'd go for option 1, even though it's a bit more work. If you must leave the data on you laptop use 2, but be aware that there's a small chance of failure of some kind.

---

### Post by mdsmedia on 2005-10-28
I installed Hoary this morning. I tried the other day (yesterday I think) and got to the partitioning part and got confused...and concerned...so I aborted. I wasn't deterred though. I liked Ubuntu Live CD and I knew if I did some research I'd work it out.

I found a link on this forum with step by step instructions on partitioning. The rest is history.

I haven't yet worked out how to add a link here, and I don't have it handy right now, but if you want I will find and post the link.

My setup was Win XP (single partition...more than 50% of 60 Gig drive free) and I'd backed up everything I thought I needed to. XP defrag left a contigious file out in the wilderness.....3/4 of the way through the drive....

I'd backed up so I went for it. Now I'm happy as Larry....I'm typing this in Firefox on XP but I haven't released the handcuffs yet. Now we're installed so the sky's the limit.

---

### Post by atoponce on 2005-10-29
[quote=Schmoopie]I've heard both ideas - that Ubuntu will erase everything when partitioning, and that Ubuntu will NOT erase everything wehn partitioning.  Which is true?

Kuecker a.k.a. Schmoopie[/quote] 
There is a menu option that allows you to either setup partioning automatically or manually.  If manually, you can select which partition you want to install Ubuntu on.  Once selected, you can delete the data on that parition, and then have the Ubuntu partitioning manager automatically allocate the free space.  This is recommended.  Then just finish the installer from there.

So in answer to your question- yes.  You can erase everything or you can leave everything.  It all depends on the menu options you select.

---

### Post by kingsidy on 2005-10-30
Using partition magic, create the partition to whatever size you want. Also for the latter to ext filesystem using partition magic. Then install Ubuntu while selecting the manual partitioning and it will pick up the ext and the swap automatically. It should install without any problem.

---

### Post by mdsmedia on 2005-10-30
[QUOTE=kingsidy]Using partition magic, create the partition to whatever size you want. Also for the latter to ext filesystem using partition magic. Then install Ubuntu while selecting the manual partitioning and it will pick up the ext and the swap automatically. It should install without any problem.[/QUOTE]

I tried to avoid Partition Magic. The install CD did it all for me. When you reach the section on partitioning in the installation, resize the existing partition (after backing up all your data and defragging your "old partition" in windows), then let Ubuntu create (format) the new partition.

It's easy to say "using partition magic" but if you don't have it you don't need it :)

---

### Post by Schmoopie on 2005-11-01
> Then use the rest as a fat32 partition to share between windows and ubuntu.

so I've got a FAT32 partition that windows recognizes, but how do I get Ubuntu to recognize it?

Kuecker a.k.a. Schmoopie

---

### Post by LHZ on 2005-11-02
[http://www.ubuntuguide.org/#mountunmountfat]("http://www.ubuntuguide.org/#mountunmountfat")
ubuntuguide.org is your friend.

---

### Post by Schmoopie on 2005-11-15
[QUOTE=LHZ][http://www.ubuntuguide.org/#mountunmountfat]("http://www.ubuntuguide.org/#mountunmountfat")
ubuntuguide.org is your friend.[/QUOTE]

I've tried both ways to mount and get nothing.  When I edit fstab, and reboot, I get sonething about "line 8 in fstab is invalid".  I checked the partition list - i know that the fat32 is dev/hda5.  I've entered everything else in the same, but no luck.  Now what?

Kuecker a.k.a. Schmoopie

---

### Post by aysiu on 2005-11-15
Post the output of these two commands ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

---

### Post by Schmoopie on 2005-11-17
[QUOTE=aysiu]Post the output of these two commands ```
sudo fdisk -l
```[/QUOTE]

Results:  
I should let you know that I've got the partition I would like to mount in Ubuntu as NTFS, but will be changing it back to FAT32 shortly.
```
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2086    16755763+   7  HPFS/NTFS
/dev/hda2            2087        3427    10771582+   f  W95 Ext'd (LBA)
/dev/hda3            3428        3707     2249100   83  Linux
/dev/hda5            2087        3361    10241406    7  HPFS/NTFS
/dev/hda6            3362        3427      530113+  82  Linux swap / Solaris
```


>  and ```
cat /etc/fstab
```

Results:  
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda5       /media/windows  vfat    iocharset=utf8,umask=000   0       0

```

I'm trying ... please help.

---

### Post by Yoda_Oz on 2005-11-17
dude, its seems that your /dev/hda5 is in fact ntfs but your fstab is trying to mount it as fat32. you need to either:
1. convert your ntfs drive to fat32, or
2. alter your fstab so that it mounts /dev/hda5 as ntfs. (dont ask me how to do that because i've never used ntfs through linux. i have a usb drive automatically mounted as ntfs. my mtab says these options:
"/dev/sda2 /media/NTFS ntfs rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0"
so maybe if you type that into your /etc/fstab but as /dev/hda5 instead.

---

### Post by Schmoopie on 2005-11-17
As I said before:  
[QUOTE=Schmoopie]I should let you know that I've got the partition I would like to mount in Ubuntu as NTFS, but will be changing it back to FAT32 shortly.[/QUOTE]

When I had the original problem, it was FAT32, and will be again soon.  I was setting up some other programs, and made it NTFS for the time being.  Let me know.

---

### Post by Yoda_Oz on 2005-11-17
cant help you until your fstab matches your filesystem type.

---

