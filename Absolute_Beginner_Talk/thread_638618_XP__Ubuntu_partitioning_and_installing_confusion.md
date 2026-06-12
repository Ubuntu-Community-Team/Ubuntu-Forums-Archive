---
title: "XP / Ubuntu partitioning and installing confusion"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Jeenyus on 2007-12-12
Over the last week or so I've been reading many articles about partitioning hard drives for XP / Ubuntu dual boot and I've come to the conclusion that it is something I would like to try.  However many of the articles have has contradicting facts, most likely due to being outdated.  The one idea that struck me as the best for my situation was partitioning the HDD into XP / Ubuntu / a FAT32 shared / and then the Swap.  The FAT32 would hold my music and other assorted media files and files I would like to access in both Ubuntu and Windows.  I've also come across articles stating that Ubuntu 7.10 can now read/write to NTFS so the FAT32 partition isn't necessary.  I've also been slightly confused on how to go about partitioning, but I think the best way for me is the Ubuntu partitioner on the install CD instead of trying to manually partition the HDD for fear of ruining the XP partition.  I've also read different opinions about the size the different partitions should be.  I have a HP zv6000 Laptop w/ AMD Athalon 64 3200+, 512 RAM, and 80 GB HDD (approx. 20GB used by the XP partition after cleaning up and running multiple defrags)  If anyone could clarify some of my confusion or has any tips before I dive into this process it would be greatly appreciated.

Much Thanks,
  Jeenyus

---

### Post by leedsdevil on 2007-12-12
i m not sure but i would suggest looking up gpartioner and grab the info from there its the same as on you r install disk maybe that will give better in site

---

### Post by Partyboi2 on 2007-12-12
Gusty can read/write ntfs, Feisty can also but you would need to install a package called ntfs-config.
.

---

### Post by Niniel on 2007-12-12
Do NOT use the automatic install, use the manual partitioning process, or else the tool will repartition the entire drive for Ubuntu, killing your XP!

The partitioner is really easy to use though, and you can review your changes before you apply them, so don't be afraid to go that route. 

Yes, Ubuntu 7.10 can read/write to NTFS out of the box, so there's no need for messing around with FAT anything. 
That also means that you don't really need a extra partition to share data, you could just make the Windows partition larger. That would have the advantage that in Windows you could stick to the default settings instead of having to change the My Documents folder and its subfolders to a different location (can be done with Tweak UI). 
On the other hand, a separate data partition could better survive you messing up Windows, so that's not a bad idea.

Partitioning depends on how you want to use your system. You could try to keep just the core OS on the Windows drive and move programs to your new data partition. In that case you could keep the Windows drive smaller; otherwise you'd have to reserve a good chuck of space for future expansion.

For Ubuntu itself, you can set aside as little as 5 GB, plus 0.5 - 1 GB for a swap partition (in my experience 512 MB is enough, even that is almost never used on my 512MB RAM notebook). If you see yourself installing a lot of software, you could double that to 10 GB, but just installing from the live CD took about 3.2 GB for me. 

So, depending on which way you want to go, you could a) shrink the Windows partition and create about 10 GB of free space for Ubuntu, or b) shrink the Windows partition to 30 - 40 GB and in the free space create a 10 GB Ubuntu partition at the end, and a swap partition, and use the remaining 30 - 40 GB as a shared data partition, to be NTFS partitioned.

---

### Post by shadow-of-sin on 2007-12-12
If you're creating a shared partition then I recommend that you do **not** use NTFS or FAT32- EXT3 is much superior (eg it is journaled so no errors when your computer is shutdown prematurely). Linux can read/write to ext3 natively and you can get a plugin for Windows in order to use the shared ext3 partition.

---

### Post by hyper_ch on 2007-12-12
The automatic install will not directly erase your whole harddisk. It will only do so if you select "use full disk"...

Basically I would recommend you this:

**(1) Make a backup** (it's always a good idea to make backups on a regular base... prefereably automatically onto a different computer....)

(2) Defrag your disk drive. In windows open the windows explorer, right-click the drive, select properties and go to the extras tab. There select defrag. Do this 2-3 times!

(3) Then partition your disk. In windows you can use Partition Magic (I used it a lot and never had problems with it, however it is not freeware and you'd have to pay for it ...).
So far I assume you have just 1 huge windows partition, maybe a hidden rescue partition.
Make the one hugs windows partition smaller and apply the settings. Don't delete it, just resize that one! Leave enough space for Linux (at least 4 GB, more is welcomed...)

(4) The simplest way then would be to start the install cd or live cd and at the partitioning scheme select "USE LARGEST CONTINOUSOUS EMPTY DISK SPACE" or somethign similar.
That will NOT erase the windows partition (and hidden one if there is one) and setup everything.

However with that option you will not get a seperate /home partition (that's recommended but not necessary). For beginners or if you want to try out, I wouldn't bother too much about it.

It's also very likely that you'll break your system the first time... well, I did but I learnt much from it. So if you decided to really use linux, I'd advice a clean install anyway and at THAT point setup a seperate home partition.

---

### Post by skymera on 2007-12-12
persoanlly i'd only resize windows. in windows.

i resized my laptops XP using using ubuntu live cd and it corrupted it. i didnt care as it run terrible.

but use partition magic in XP or something.

---

### Post by Niniel on 2007-12-12
> **shadow-of-sin said:**
> If you're creating a shared partition then I recommend that you do **not** use NTFS or FAT32- EXT3 is much superior (eg it is journaled so no errors when your computer is shutdown prematurely). Linux can read/write to ext3 natively and you can get a plugin for Windows in order to use the shared ext3 partition.

NTFS has file system journaling, and since Ubuntu 7.10 comes with built-in support, you wouldn't have to mess with any plugins. Unless you consider yourself an advanced user, I think it would be better to just use NTFS and rely on Ubuntu being able to read/write Windows drives.

---

### Post by Niniel on 2007-12-12
> **hyper_ch said:**
> 
(2) Defrag your disk drive. In windows open the windows explorer, right-click the drive, select properties and go to the extras tab. There select defrag. Do this 2-3 times!


Totally useless.

The built-in Windows defragger just does that - it defrags, but it doesn't move data to the front of the drive. There are tools that claim they do that though, even free ones.

---

### Post by Niniel on 2007-12-12
> **skymera said:**
> persoanlly i'd only resize windows. in windows.

i resized my laptops XP using using ubuntu live cd and it corrupted it. i didnt care as it run terrible.

but use partition magic in XP or something.

I have to disagree. 
I used the Live CD partitioner, which is essentially a PM clone, and it worked beautifully (manual mode). No problems whatsoever. It's free, it's on the CD, it's easy to use - I don't see any reason to not use it.

---

### Post by Jeenyus on 2007-12-12
Thanks for all the input guys.  I think the setup I'm leaning towards now is  XP partition (aprox. 30GB)  Ubuntu partition (approx. 15GB)  Swap (1GB) and Shared NTFS (rest of space, about 34ish GB).  I've backed up my system already so I'm not too worried about that.  I've also ran defrag 4 times now and I might give JkDfrag a shot (if anyone has any input about this product it would be appreciated)  I would like the try and stick with the partitioner on the Ubuntu CD, mainly because its free, and the tutorials I have found do a pretty good job explaining the process.  Hyper_ch mentioned that this would not let me have the /home partition for Ubuntu, is there any way to keep my XP partition and have the separate /home partition for Ubuntu?  I've left 15GB of space for Ubuntu, which from what I've read seams like a lot, but I plan on trying a lot of the software that Ubuntu has to offer to really get a feel for the system.  I want to become completely independent from Windows (at least on my personal computer) and this is sort of my first step in doing so.  Thanks again for all the help.:)

---

### Post by ByteJuggler on 2007-12-12
vOptXP is a pretty decent Windows defragger that I think you can coax into putting all the files at the beginning of your disk.

---

### Post by Jeenyus on 2007-12-12
> **Niniel said:**
> Totally useless.

The built-in Windows defragger just does that - it defrags, but it doesn't move data to the front of the drive. There are tools that claim they do that though, even free ones.

I've already defraged about 3-4 times, and also defraged in Windows Safe Mode (recommendation from an article I read) and the image that the defragger shows gets smaller and moves towards the left of the space shown.  I interpret this as moving to the front of the disk, am I wrong?  And also, when manually partitioning, does the size you are able to scale the partition down to rely on the amount of space on the drive or where the data is located on the drive?  I guess what I'm asking is if my drive has 20GB used of 80GB total, but the defragger image shows the data spread over approx. 50% of the HDD, can i resize down to 25% or only to 50%?

---

### Post by Jeenyus on 2007-12-12
I've also heard about problem with GRUB and the MBR and completely ruining the XP partition.  I'm not sure exactly what this means or when/why it would happen but if anyone has any comments on that it would be appreciated.  Thanks you.

---

### Post by Niniel on 2007-12-12
Normally, there shouldn't be a problem with Grub. It'll install into the drive's MBR, but as long as it recognized Windows that's ok. It'll auto-create an entry in its boot menu for Windows.
If there is a problem, it won't do anything to the actual Windows installation, you just won't be able to boot into it. Can be solved very easily by restoring the MBR.

As for defragging Windows, it doesn't matter how often you do that. You can run it eternally, and it won't consolidate your data other than what is required for defragging. It just can't do it. It's a stripped down version of Diskkeeper, and that functionality has been removed. The graphics are just there to show you that something is going on. 
To my knowledge, resizing does indeed depend on where data is located. Shouldn't be a problem though unless you had a ton of stuff on your hd and then deleted most of it except for the most recently installed items. 
Not sure if the partitioner moves data prior to resizing... it might even do that.

---

### Post by hyper_ch on 2007-12-12
> **Niniel said:**
> Totally useless.

The built-in Windows defragger just does that - it defrags, but it doesn't move data to the front of the drive. There are tools that claim they do that though, even free ones.

it's the windows defragger I'm talking about :popcorn:

---

### Post by ubutufan on 2007-12-12
I am using GPARTED to create and or resize partitions. It works like a charm and you also get a terminal to enter some basic commands

---

### Post by Partyboi2 on 2007-12-12
Jeenyus

> Hyper_ch mentioned that this would not let me have the /home partition for Ubuntu, is there any way to keep my XP partition and have the separate /home partition for Ubuntu?
if you choose to manually configure your partitions instead of the "Use largest continousous empty disk space" You would have the option to create a seperate /home partition for ubuntu. But you can always create a seperate /home partition later
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

