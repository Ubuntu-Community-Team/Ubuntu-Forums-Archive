---
title: "Primary/Logical Partition Question"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by stevenash on 2006-05-17
I believe I'm going to partition my 250GB hard drive like this...tell me if it looks alright, please:

10GB ext3 / root - primary (bootable flag on)
20GB ext3 /home - logical
1GB SWAP - logical
219 NTFS - primary

Do all those look okay?  I don't know where I should mount the NTFS partition to.  I just want to use it to store media files on that can be read by Linux.

---

### Post by joshrobinson on 2006-05-17
[QUOTE=stevenash]I believe I'm going to partition my 250GB hard drive like this...tell me if it looks alright, please:

10GB ext3 / root - primary (bootable flag on)
20GB ext3 /home - logical
1GB SWAP - logical
219 NTFS - primary

Do all those look okay?  I don't know where I should mount the NTFS partition to.  I just want to use it to store media files on that can be read by Linux.[/QUOTE]

looks fine to me, but how much ram do you have? your swap space should be 2x what you have in ram

also if you plan on installing alot of things on your system you could always bump up your root partition to 15 or 20.. but in linux that kinda space will last a good while

---

### Post by Sef on 2006-05-17
> I believe I'm going to partition my 250GB hard drive like this...tell me if it looks alright, please:

10GB ext3 / root - primary (bootable flag on)
20GB ext3 /home - logical
1GB SWAP - logical
219 NTFS - primary

Do all those look okay?

Windows needs to be on the first partition.  As long as it is.  You will do fine.

If you have 1 GB ram, then you really won't need swap unless you are planning on doing video editing or heavy duty gaming.

---

### Post by Sutekh on 2006-05-17
[quote=stevenash]I believe I'm going to partition my 250GB hard drive like this...tell me if it looks alright, please:

10GB ext3 / root - primary (bootable flag on)
20GB ext3 /home - logical
1GB SWAP - logical
219 NTFS - primary

Do all those look okay? I don't know where I should mount the NTFS partition to. I just want to use it to store media files on that can be read by Linux.[/quote] Looks fine. 1GB of swap will be plenty. I rarely dip into my swap, and I have 512MB RAM.

I agree with joshrobinson, you might want to give more to the root partition.  This is where all your applications/programs will come under.   Does Windows really need 219GB? 


The other thing to consider is a FAT partition, that Windows and Linux can both write to.  Linux can't write to the NTFS one.

You can set the mount point for the NTFS partition in the installer, **or** you can do it later on, when you are in Ubuntu.  You will have to wait until then before you can sort out the modes of access/permissions to the NTFS partition anyway, so I'd say don't worry to mch about setting the mount point **until** you have Ubuntu installed.


If you haven't already come across it, this is a great site for a Ubuntu/Windows dual boot, as well as seprate /home partitions.

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

Best of Luck!

---

### Post by joshrobinson on 2006-05-17
[QUOTE=Sef]Windows needs to be on the first partition.  As long as it is.  You will do fine.

If you have 1 GB ram, then you really won't need swap unless you are planning on doing video editing or heavy duty gaming.[/QUOTE]

i do massive video editing here.. so i have alot of swap on my desktop.. so i like to have it.. i guess i should have asked if he was gona be RUNNING windows, or was just accessing files off the hard-drive

if you arent gona use windows you could always use fat32 (vfat in linux) so then you can write to the drive also, and windows can still run on it if you need it, but you have to reinstall windows

---

### Post by stevenash on 2006-05-17
[QUOTE=joshrobinson]i do massive video editing here.. so i have alot of swap on my desktop.. so i like to have it.. i guess i should have asked if he was gona be RUNNING windows, or was just accessing files off the hard-drive

if you arent gona use windows you could always use fat32 (vfat in linux) so then you can write to the drive also, and windows can still run on it if you need it, but you have to reinstall windows[/QUOTE]

First, thanks to all for your help and opinions.

I have 512MB or ram, so I suppose I could just make the SWAP 512MB right?

I'm going to use the 219GB just for storage of media files basically.  When I am in the partitioner during the Ubuntu installation, should I make the 219GB vfat?  Will Windows be able to read it?

---

### Post by Sutekh on 2006-05-17
There is no real guideline (of that I'm aware) about the swap : RAM ratio. It could be more hassle if you don't have enough, than if you have wasted swap space. If you can spare 1GB, I don't think you'd ever run into trouble.

So this partition is for media files only? You are not putting Windows on it? You never actually said, and we all assumed that you were. 

I think it's best not to create a vfat partition with the Ubuntu installer. I've had problems with Windows recognising them as such. Use Windows to create the FAT partition, Ubuntu should have no problems accessing that.

---

### Post by RRS on 2006-05-17
Yes, both Windows and Linux can read and write vfat.

How large are your files? The main disadvantage of vfat seems to be a limit on file size, 4m if I recall (but not sure exactly), could be a problem for movies.

If that's an issue maybe someone could suggest another option, otherwise vfat would seem best.

---

### Post by stevenash on 2006-05-18
[QUOTE=Sutekh]There is no real guideline (of that I'm aware) about the swap : RAM ratio. It could be more hassle if you don't have enough, than if you have wasted swap space. If you can spare 1GB, I don't think you'd ever run into trouble.

So this partition is for media files only? You are not putting Windows on it? You never actually said, and we all assumed that you were. 

I think it's best not to create a vfat partition with the Ubuntu installer. I've had problems with Windows recognising them as such. Use Windows to create the FAT partition, Ubuntu should have no problems accessing that.[/QUOTE]
Sorry.  I have 2 hard drives.  The first is a 40GB drive with Windows installed on it.  The other is the 250GB that right now I use for storing files (music media mostly) and am hoping to use to try out Linux.

---

### Post by zba78 on 2006-05-18
That should be fine. To give you an idea my Kubuntu Dapper root is 12GB (reiserFS), home is 36GB reiserFS and WinXP home is aroung 10GB fat32 (came pre-installed on my laptop).

Theres also a spare 10GB fat 32 that I need to do something about.

Oh and because I have 1GB RAM I only decided to go for a 512MB swap (1.5GB ram total is more then plenty). Bit of a waste really, I've ran distros on my old 512MB RAM PC with no swap and never had any problems.

---

### Post by Sutekh on 2006-05-18
[quote=stevenash]Sorry. I have 2 hard drives. The first is a 40GB drive with Windows installed on it. The other is the 250GB that right now I use for storing files (music media mostly) and am hoping to use to try out Linux.[/quote] Cool, in that case use Windows to create the FAT partition. You can always get access to it through Ubuntu, by creating it in Windows you can ensure that it will work there. 

Whether you do this before or after installing Ubuntu, doesn't really matter.

There may be an issue with a FAT partition of that size.  I'm pretty sure that FAT partitions *can* be up to 2TB in theory, however the Windows partitioning program will only allow a 32B partition to be created.  

Why?  Who knows. [http://support.microsoft.com/kb/184006/en-us]("http://support.microsoft.com/kb/184006/en-us")

I know that a FAT partition created not with Windows, say with the [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") can be larger than 32GB, but I have had cases, where Windows did not recognise these partitions.  Partition Magic might also be able to create partitions larger than 32GB, so that could be an option too.

The other option, is to format the partition with ext3 and use a program like [Ext2 IFS for Windows]("http://www.fs-driver.org/") to get access to the partition.

---

