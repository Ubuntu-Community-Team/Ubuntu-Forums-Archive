---
title: "Partition strategy for XP/Ubuntu system"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by noldguy on 2006-10-30
I want to install Ubuntu and XP on a new PC I am building (250gb drive, 1 or 2gb RAM). Can /home be a fat32 partition where I'll keep all my Win and Ubuntu data files? i.e. something like:

1. 10-15gb ext3 / partition for Unbuntu
2. 1gb swap
3. 10gb ntfs windows partition
4. remainder to /home fat32

---

### Post by bulldog on 2006-10-30
Shouldn't try to make your /home a fat32 partition.

Just make it ext3 and create a separate fat32 for your win en ubu backups.

---

### Post by Kateikyoushi on 2006-10-30
There is no need to make your /home a fat32 partition, with this driver you can write to ext3 from windows. [LINK]("http://www.fs-driver.org/")

---

### Post by bsussman on 2006-10-30
I believe it would work, but it is unusual to have home not be a linux type.

I would have left the win data in the 1 ntfs partition or a separate vfat partiton used for pivot (read/write both sides), mounted and soft linked to make it appear in the home directory.

What are you actually planning to do with this system?  Why is it important to have the win and linux files in the same directory?

---

### Post by masav5 on 2006-10-30
I have 2 80gb SATA hd's connected via RAID to be seen as 1 hd.  When I installed Ubuntu 6.06, I partitioned the second drive into 3 parts:

/home - 55gb - ext3 - I also intend to use this for shared files between xp and Ubuntu.

/ - root 20gb - ext3

swap - 2gb

I left the first hd as is, that's where my xp install is.

After first installing, I was getting an error 21 from grub when it tried to boot.  I deleted the boot array that was set up, and now Linux works fine.  Only problem is I can see anything on sda.  Not only that, xp is no longer a boot option.  I checked the forums, and the closest thing I could find was some instructions on how to mount to an ntfs partition.  But I can't even see the partition on sda.  (I mean, when I look at it from Linux, there's no sda1 etc.,  it only says sda, and that it can't mount.)  I'm getting myself confused now.  If this makes sens to anyone, please let me know.  All my files are on that first drive, and I'm at a loss.

---

### Post by Sef on 2006-10-30
> After first installing, I was getting an error 21 from grub when it tried to boot. I deleted the boot array that was set up, and now Linux works fine. Only problem is I can see anything on sda. Not only that, xp is no longer a boot option. I checked the forums, and the closest thing I could find was some instructions on how to mount to an ntfs partition. But I can't even see the partition on sda. (I mean, when I look at it from Linux, there's no sda1 etc., it only says sda, and that it can't mount.) I'm getting myself confused now. If this makes sens to anyone, please let me know. All my files are on that first drive, and I'm at a loss.

Is Windows on the first partition?  If not, that is likely your problem.

> an error 21 from grub

Here it is

> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

---

### Post by noldguy on 2006-10-30
> What are you actually planning to do with this system? Why is it important to have the win and linux files in the same directory?
Most of my files are not unique to windows...i.e. mp3,images,txt, doc, pdf, html/php, etc. Even though I plan on Ubuntu as my primary system when I do have to work in XP I want to access the  "generic" files. 

I am used to working with one xp partition and one partition allocated solely to my data files. I would like to keep it that way unless there is some reason not to.

Having followed Kateikyoushi's link it looks to me like ext2 IFS for Windows may be the way to go. That would make my ext3 /home partition accessible to XP.

> separate vfat partiton used for pivot (read/write both sides), mounted and soft linked to make it appear in the home directory
I understand soft linking but I don't understand "vfat" and "pivot (read/write both sides)". Can someone enlighten me.

---

### Post by Adramelech on 2006-10-30
2gb swap???
1Gb swap??

Isn't that too much?? i have 250 or 300mb i think. Theres a way to know how big your swap should be?

---

### Post by Nut on 2006-10-30
Make sure Windows isn't taking up your whole hard drive. Make a swap partition twice the size of your computer's ram, and a ext3 partition with the remaining part of your hard drive.

Easy stuff.

Basically, here are your partitions, with 500 MB ram and a 100 GB hard drive.

Partition 1 (Windows)
Size: 50 GB
Type: NTFS (automatically formatted to this type. you don't need to mess with it.)

Partition 2 (linux file sys)
Size: 49 GB
Type: ext3
whatchamacallit: / (root)
Primary

Partition 3 (linux swap)
size: 1 gb
type: swap (linux-swap)
whatchamacallit: /swap or whatever.
when you make the partition it will AUTOMATICALLY make the swap /swap and the ext3 / (ROOT).
primary

yeah, that's it.

it's actually easier than you think. you really don't need to mess with anything after making the partitions manually on the livecd. it may have more than one partition for windows though. mine doesn't as i installed it myself and i made one partition of half my hard drive and during the installation it formats it to NTFS itself.

but, that's all you need. as soon as my server gets running i'll let you know of a tutorial i'm going to write of it.

---

### Post by bsussman on 2006-10-31
> **noldguy said:**
> 
I understand soft linking but I don't understand "vfat" and "pivot (read/write both sides)". Can someone enlighten me.

vfat is a windows format that can be safely read/written from the linux side.  NTFS may still exhibit problems, used this way and I refrain from using it for shared filesystems.

pivot is a generic term for a data area that is used to share between two almost separate systems.

---

### Post by ljpm on 2006-10-31
> **Adramelech said:**
> 2gb swap???
1Gb swap??

Isn't that too much?? i have 250 or 300mb i think. Theres a way to know how big your swap should be?

Typically swap is twice your ram. ie. 1 Gb for 512 mb ram.

---

