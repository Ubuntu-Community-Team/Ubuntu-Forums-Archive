---
title: "/home partition.... what is it?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by agerfe on 2007-12-03
I will soon be installing Ubuntu Studio on my second hard drive.

A member of this forum was kind enough to write down the necessary instructions to create this dual boot system. [http://ubuntuforums.org/showthread.php?t=608162]("http://ubuntuforums.org/showthread.php?t=608162")

He suggests that I create the partitions manually but doesn't specify the size of the /home partition and the purpose of this partition is not entirely clear in his post.

What is this partition for? What will be stored in there? How big should it be?

I will be storing all my info (documents, images, audio and video files, etc) in a separate partition that will be shared by Windows and Ubuntu.

Will appreciate any help.

agerfe

---

### Post by mikewhatever on 2007-12-03
/home is similar to Documents and Settings in Windows. You personal settings and configurations are stored there, plus, every user gets a separate home. The size very much depends on the size of your HDD, your needs and the amount of unallocated space available. I can't really specify a number. Right now, the contents of my home directory, personal files excluded, occupy less then 10 MB.

---

### Post by ericesque on 2007-12-03
funny, you should mention your docs, photos, music, etc.   That is exactly what the /home partition is intended for.  

Equate it to My Documents in Windows.  Ubuntu will automatically create a handful of folders on the /home partition including Documents, Images, Videos and Music.

---

### Post by yeehi on 2007-12-03
A /home partition is a dedicated space on your hard drive. It is a good idea for many reasons:

1) Each user on the computer can have their own home, set up the way they like, with their files not ordinarily viewable by others, their defaults for prefered programs and so on.

2) If you screw up your /home/your_username area, you can easily delte that user and create a new user, without effecting the whole installation of ubuntu.

3) If you screw up the installation of ubuntu, you can format the installation, but leave the home partition unformatted, so your data files are not lost. 

NB - Generally speaking you would want to allocate a large amount of space to /home, hundreds of gigabytes, if possible. 

Other partitions include the swap partition: that should be double the size of your memory, your /boot partition, which for multi-boot systems I have read should be about 800MB in size.

Getting familiar with the sort of contents in each of the different partitions is a good thing on which to spend a bit of time.

---

### Post by tact on 2007-12-03
> **agerfe said:**
> I will soon be installing Ubuntu Studio on my second hard drive.
[...]
I will be storing all my info (documents, images, audio and video files, etc) in a separate partition that will be shared by Windows and Ubuntu.

Will appreciate any help.

agerfe

Make that partition your home partition.

Adding to what others said - whenever you create a new user (give an account to someone else to use your machine) by default all their personal folders and configurations will go into the home partition also.  So it needs to be as big as what you expect you plus all your other users may want in the way of personal space.

---

### Post by agerfe on 2007-12-03
Sounds like a great idea but I need to format that partition as NTFS because it will be shared by Windows and Ubuntu.

Will Ubuntu accept a /home partition with NTFS format instead of EXT3?

Also, if I want to install another distribution in the future I will have to create more partitions inside that partition. Is this safe? Could my data be deleted in the process?

agerfe

---

### Post by agerfe on 2007-12-03
By the way..... there will be no more users in the future. I use this computer to work and need it to be available for this 24/7. Also the type of work I do requires a lot of space so I can't make room for any other user. Just can't afford to. 

Not that I don't let others use my comp. Of course I do! :)  But sharing it with others is just not possible!

agerfe

---

### Post by CatKiller on 2007-12-03
> **agerfe said:**
> Will Ubuntu accept a /home partition with NTFS format instead of EXT3?

Absolutely not. ext3 and ReiserFS both have features that NTFS lacks. It's possible to install a driver in Windows so that Windows can read ext3 though.

> Also, if I want to install another distribution in the future I will have to create more partitions inside that partition. Is this safe? Could my data be deleted in the process?


You can resize and move partitions with a tool like GParted. You wouldn't make partitions inside that partition as such, but you can make that partition smaller, then make new ones in the free space, and then mount those partitions in your Home folder, should you wish. See, for example, [this Wikipedia page]("http://en.wikipedia.org/wiki/Disk_partitioning") that explains Primary and Extended partitions.

> **agerfe said:**
> By the way..... there will be no more users in the future. I use this computer to work and need it to be available for this 24/7. Also the type of work I do requires a lot of space so I can't make room for any other user. Just can't afford to. 

Not that I don't let others use my comp. Of course I do! :)  But sharing it with others is just not possible!

Linux was always designed with multiple users in mind. There is no reason why having another user, even another user logged in and doing stuff, would affect your workflow in any way, except in the case where you are both running resource-intensive applications in a resource-limited system.

And having a "guest" user account means that others can use your computer without affecting any of your own settings or files.

---

### Post by gn2 on 2007-12-03
It perhaps could be possible to install Ubuntu including a /home directory to a single partition then add  ntfs-3g then replace the /home directory to an NTFS formatted /home partition?

NTFS partitions can be mounted read/write as /media so why not after installing the required write driver as /home?

---

### Post by CatKiller on 2007-12-03
> **gn2 said:**
> why not after installing the required write driver as /home?

NTFS has poor user permission capabilities.

---

### Post by gn2 on 2007-12-03
> **CatKiller said:**
> NTFS has poor user permission capabilities.

I'm confused, surely the user permissions are set by the operating system that writes the files (and their permissions) and not by the file system itself?

---

### Post by agerfe on 2007-12-03
In relation to the NTFS partition.......... 

will Windows recognize my Ubuntu partitions?

This is necessary so that I can format the rest of available space as NTFS, as this partition will be shared by both OS's.

Maybe I should format as NTFS first and then create the partitions for Ubuntu with gparted. :confused:

agerfe

---

### Post by AlanRogers on 2007-12-03
Personal Bitter Experience; you cannot have a Home/Documents & Settings area shared between Linux and Windows (yet) because Linux wants a Linux file system for such a key folder and Windows wants a Windows file system for such the same reasons.
 
If you want to go down this route, my suggestion would be this:
[LIST=1]
[*]Windows OS partition (NTFS)
[*]Windows User Data partition (NTFS)
[*]Linux / (root) partition (EXT3)
[*]Linux /home partition (EXT3)
[*]Shared Documents partition (VFAT)[/LIST]Mount partition 5 within /home in Linux and map it as a separate drive or put a shortcut to it in My Documents in Windows. Your data will then be accessible from both systems but not directly referenced, and therefore corruptable, by either. Similarly, either system can be reinstalled without destroyed any user data.

---

### Post by CatKiller on 2007-12-03
> **gn2 said:**
> I'm confused, surely the user permissions are set by the operating system that writes the files (and their permissions) and not by the file system itself?

That information has to be stored somewhere. ext3 stores it in the filesystem itself. NTFS doesn't store it anywhere, as far as I can tell. I've not tried to set permissions on an NTFS filesystem from Ubuntu, since Ubuntu couldn't write to NTFS the last time I had access to a Windows computer, but I know that FAT will pretend to set permissions and then quietly forget that you mentioned it at all.

To the OP: As AlanRogers says, it's not worth the hassle to have system folders in a non-native filesystem for either environment. It's much less likely to go wrong if you have a separate partition for the data and whatnot that you want accessible from each Operating System that **doesn't** contain settings. It will show up as a separate drive in Windows, and in Ubuntu you can mount it wherever you like, including as a directory in your Home folder if you wish.

It has been traditional to have this partition as FAT, since historically Linux couldn't write to NTFS and Windows couldn't write to ext3, but neither is a problem these days.

---

### Post by agerfe on 2007-12-03
Oh no. You got me wrong guys. 

I will create a small EXT3 partition and set it as /home, where my personal settings will be stored. But no data (such as documents, photos, videos, etc. ) will be stored in there. For these I will leave the rest of the 125GB partition. (I have a 250GB hard disk already partitioned into two 125GB partitions)

Windows is installed on a separate 250GB hard disk. 

To be even more specific, I will create:

1. A root partition for Ubuntu (10GB) (EXT3)
2. A swap partition (2GB) (SWAP)
3. A /home partition (5GB) (EXT3)
4. A shared data partition (108GB) (NTFS)

I just need to know if Windows will recognize the three partitions for Ubuntu after I have created them, and let me format the remaining 108GB as NTFS.

Or maybe I should begin by formatting the whole 125GB partition as NTFS and then creating the partitions for Ubuntu with gparted.

agerfe
P.S.: somewhere I've read about a partition which needs to have the size of 2 times my RAM.... is it the swap partition?

---

### Post by The Cog on 2007-12-03
agerfe: That looks good to me. 5G for /home is perhaps larger than needed, but since applications store their settings and data there (such as Firefox's cache, and gnomes thumbnails database) maybe its about right after all. 

2G swap should be plenty. 2xRAM is just silly in my opinion as it means that systems with a RAM shortage also don't have the swap space they need either despite the fact that they need it more than systems with more RAM.

---

### Post by lespaul_rentals on 2007-12-03
Hey mate, your last post looks like a good plan.  You might not even need 10GB for your / partition, but you have plenty of space for it, so go for it.  2GB for swap and 5GB for /home should be adequate as well.

However, don't format the "shared" partition as NTFS.  Format it as FAT32.  Windows will be able to read it, Linux will be able to read it, and you won't have to mess around with NTFS drivers and file permissions.

Other than that, full speed ahead.

---

### Post by The Cog on 2007-12-03
Starting with Gutsy, writing to NTFS is enabled by default. So NTFS for a shared drive is OK.

---

### Post by lespaul_rentals on 2007-12-03
> **The Cog said:**
> Starting with Gutsy, writing to NTFS is enabled by default. So NTFS for a shared drive is OK.

Very true.  But I don't recommend Gutsy because of the plethora of problems myself and countless others are having.  ;)

---

