---
title: "Partitioning Advice"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by stevenash on 2006-06-15
I've been struggling with this for awhile, and no one has really been able to give me an answer to it.

First, it's a very long story how I got to this point and doesn't really matter anymore.  Here is where I am at:

I have 2 hard drives.  The master is a 250GB drive with about 30GB partitioned off.  I have Ubuntu installed on that partition.  My slave hard drive is a 40GB drive that is completely taken up by Windows.

Again, long story, but when I was setting up Ubuntu, I did not format the remaining 220GB of space on my master hard drive.  Now I wish to format it, but would like to be able to do the folllowing:

I want about 20GB of space to be shared between Windows/Linux.  I want to use this partition as storage space to put music, pictures, and video into so I can access the files no matter which OS I am on.

Next, I want to partition the remaining 200GB as NTFS space, that I may use for other Windows storage or to install other OS'.

Can someone PLEASE tell me what the best way to accomplish this is?  I'd like to know what type of file systems I need and the best/easiest way to partition in either Linux or Windows.

Thank you all so much for your help.

---

### Post by bruce89 on 2006-06-15
Use Gparted - [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).  The "swap" partition will have to be FAT32, as it can be read between Ubuntu and Windows.

---

### Post by stevenash on 2006-06-15
[QUOTE=bruce89]Use Gparted - [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).  The "swap" partition will have to be FAT32, as it can be read between Ubuntu and Windows.[/QUOTE]
Can the FAT32 file system support a 20GB partition?  Will it be stable/reliable?

---

### Post by anaconda on 2006-06-15
Win2000&XP support fat32 up to 32GB, so that isn't a problem. 
If you dont make the fat32 partition bigger than that then it is stable and reliable.

I have had problems with bigger than 32GB fat32 partitions and win2000.. it auto fixes then (=destroys all data), but havent heard problems with winXP..

one good choise is to use ext3 partition and install:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
to windows, so that it can access it..

---

### Post by MonkeyBoy on 2006-06-15
I have a similar but smaller setup on an 80 gig drive with about 20 gig for XP, 20 gig for Dapper, and the remaining 40 gig as a seperate NTFS partition.  I keep music, videos, pictures, etc on the 40 gig partition and I have no problems accessing files with either OS.  

It might be easier to just do your big partition as NTFS and then resize it when you need it rather than splitting it just yet.  Gparted is quite easy to play around with so it might be worth trying one big partition first to see how well it works.

---

### Post by aysiu on 2006-06-15
To Stevenash: You don't need a live CD to format that partition. Just ```
sudo aptitude update
sudo aptitude install gparted ntfsprogs gksu
gksudo gparted
``` Unmount the partition and reformat/resize it how you want.

GParted is pretty easy to figure out. The only thing that may be a bit confusing is that you need to select the drive to be able to see it. You select the drive by clicking the drive in the top-right-hand corner. A drop-down menu will appear.

---

### Post by stevenash on 2006-06-15
[QUOTE=anaconda]Win2000&XP support fat32 up to 32GB, so that isn't a problem. 
If you dont make the fat32 partition bigger than that then it is stable and reliable.

I have had problems with bigger than 32GB fat32 partitions and win2000.. it auto fixes then (=destroys all data), but havent heard problems with winXP..

one good choise is to use ext3 partition and install:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
to windows, so that it can access it..[/QUOTE]
Interesting.  I think I like this route.

Do you think it would be best if I created a 20GB ext2 partition then instealled fs-driver?

---

### Post by stevenash on 2006-06-15
[QUOTE=aysiu]To Stevenash: You don't need a live CD to format that partition. Just ```
sudo aptitude update
sudo aptitude install gparted ntfsprogs gksu
gksudo gparted
``` Unmount the partition and reformat/resize it how you want.

GParted is pretty easy to figure out. The only thing that may be a bit confusing is that you need to select the drive to be able to see it. You select the drive by clicking the drive in the top-right-hand corner. A drop-down menu will appear.[/QUOTE]

Thanks for the advice, aysiu.

[QUOTE=MonkeyBoy]I have a similar but smaller setup on an 80 gig drive with about 20 gig for XP, 20 gig for Dapper, and the remaining 40 gig as a seperate NTFS partition.  I keep music, videos, pictures, etc on the 40 gig partition and I have no problems accessing files with either OS.  

It might be easier to just do your big partition as NTFS and then resize it when you need it rather than splitting it just yet.  Gparted is quite easy to play around with so it might be worth trying one big partition first to see how well it works.[/QUOTE]
So you are able to both read and write to an NTFS file system with Windows AND Linux?  I didn't know you could do that with the NTFS system.  Or do you have something else installed that allows you to do it?

---

### Post by aysiu on 2006-06-15
There's really no point in having a 20 GB partition if you're going to install FS-Drive r in Windows. The whole point of FS-Driver is to give Windows read/write access to Ext3.

Just make the huge 220 GB partition Ext3, and both Ubuntu and Windows can use it.

---

### Post by stevenash on 2006-06-15
[QUOTE=aysiu]There's really no point in having a 20 GB partition if you're going to install FS-Drive r in Windows. The whole point of FS-Driver is to give Windows read/write access to Ext3.

Just make the huge 220 GB partition Ext3, and both Ubuntu and Windows can use it.[/QUOTE]
Sometimes I make things too complicated.  Thanks for simplifying it for me.  I will try it that way when I get home today.  I will make the partition using gparted.  If I'm too stupid to get it to work I'll try the FAT32 method.

Thanks everyone for your help.

---

### Post by aysiu on 2006-06-15
[QUOTE=stevenash]Sometimes I make things too complicated.  Thanks for simplifying it for me.  I will try it that way when I get home today.  I will make the partition using gparted.  If I'm too stupid to get it to work I'll try the FAT32 method.

Thanks everyone for your help.[/QUOTE] I would highly advise against FAT32 in this case. > I want to use this partition as storage space to put music, pictures, and video If your videos are bigger than 4 GB, FAT32 cannot handle that large a file size.

Also, with a partition size as large as 220 GB, it will get extremely fragmented in FAT32, unlike in Ext3, which doesn't get as fragmented over time.

Once you format the partition as Ext3, read this to get it properly mounted in Ubuntu:
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by stevenash on 2006-06-15
Okay, I have some problems.

I got to GParted fine.  I had a big block in there titled Unallocated Space.  I clicked New, and made a new ext3 partition using the entire Unallocated Space.  I clicked Apply and it worked for awhile.  Eventually it gave me a Warning:

"At least one operation was applied to a busy device.

A busy device is a device with at least one mounted partition.
Because making changes to a busy device may confuse the kernel, you are advised to reboot your computer."

So I reboot my computer, and eventually it starts giving the following error:

Buffer I/O error on device dm-5, logical block 6326762

It keeps scrolling that error for about 100 blocks, then goes on and boots up.

Anyone know what that is all about?

Also, as soon as I got finished making the partition, somehow GParted showed 3,408 MB already used in the partition I just created.  There shouldn't be anything on there yet.

Now I've tried to mount it, and followed all the steps in the link provided above, but I'm not sure if it actually got mounted.  How can I tell?  Under "Filesystem" there is a "storage" folder, which is what I tried to mount the partition to, but it only says there is 6.8 GB of free space.  

Anyone have some suggestions?

---

### Post by stevenash on 2006-06-15
[QUOTE=stevenash]Okay, I have some problems.

I got to GParted fine.  I had a big block in there titled Unallocated Space.  I clicked New, and made a new ext3 partition using the entire Unallocated Space.  I clicked Apply and it worked for awhile.  Eventually it gave me a Warning and something about the new partition being "busy" and it was recommended that I reboot. 

So I reboot my computer, and eventually it starts giving the following error:

Buffer I/O error on device dm-5, logical block 6326762

It keeps scrolling that error for about 100 blocks, then goes on and boots up.

Anyone know what that is all about?

Also, as soon as I got finished making the partition, somehow GParted showed 3,408 MB already used in the partition I just created.  There shouldn't be anything on there yet.

Now I've tried to mount it, and followed all the steps in the link provided above, but I'm not sure if it actually got mounted.  How can I tell?  Under "Filesystem" there is a "storage" folder, which is what I tried to mount the partition to, but it only says there is 6.8 GB of free space.  

Anyone have some suggestions?[/QUOTE]

Actualy, I have an update:

I refreshed my drives list in GParted, and the partition I just created has a Warning:

Warning: Unable to read the contents of this filesystem!  Because of this some operations may be unavailable.

Also, it displays the Status as Not Mounted.  

:sad:

---

### Post by stevenash on 2006-06-15
Another update:

I deleted the partition and started over.  It gave me the "Busy Device" message again, but this time as soon as I was finished I was able to mount the drive correctly.

For some reason, as soon as I formatted, 3,408MB were used again.  Then after I mounted, 13,853 MB were used.  However, there is nothing in the /storage folder except a lost+found folder with nothing in it.

Then, I decided to restart my computer.

Once again, when it got to Starting Enterprise Volume, it gave me the "Buffer I/O error on device dm-5, logical block 6326XXX" again.

Any idea what this error is?  Other than that and the 13,000 MB that are mysteriously used up, the drive looks/works fine.

---

### Post by stevenash on 2006-06-15
So sorry to do this, but bump.

---

### Post by aysiu on 2006-06-15
You're not the first person to encounter problems with the live CD's GParted.

I know it's a pain in the *** to download another distro, but I've never had a problem with PCLinuxOS's DiskDrake.

When I need to do partitioning stuff, I boot up PCLinuxOS, use DiskDrake. Then I reboot and install Ubuntu.

---

### Post by stevenash on 2006-06-15
[QUOTE=aysiu]You're not the first person to encounter problems with the live CD's GParted.

I know it's a pain in the *** to download another distro, but I've never had a problem with PCLinuxOS's DiskDrake.

When I need to do partitioning stuff, I boot up PCLinuxOS, use DiskDrake. Then I reboot and install Ubuntu.[/QUOTE]
I don't believe I'm using live CD.  I followed the steps you told me to.  I'm just surprised that no one knows what the "Buffer I/O error on device dm-5, logical block 6326###" means.  Very strange.

---

### Post by aysiu on 2006-06-15
You're not using the live CD?

So you're using the Alternate Install CD? Then I'm really surprised you're running into these errors.

---

### Post by stevenash on 2006-06-15
[QUOTE=aysiu]You're not using the live CD?

So you're using the Alternate Install CD? Then I'm really surprised you're running into these errors.[/QUOTE]
Sorry, I'm a newb.  Here is how I'm getting to GParted:

First I did this:
sudo aptitude update
sudo aptitude install gparted ntfsprogs gksu

Now I type this to run it:
gksudo gparted

---

### Post by aysiu on 2006-06-15
I'm sorry. I'm confused.

You already have Ubuntu installed.

You know... a live CD may not be a bad idea. I realize you can unmount any partition you're not using, but you may be getting weird "device is busy" messages even though the partitions are unmounted.

---

