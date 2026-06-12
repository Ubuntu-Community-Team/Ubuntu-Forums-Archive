---
title: "HEEELP!!! Partioning screw-up :'("
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by __a on 2006-07-31
Okay, I'm in _deep_ trouble now yall:

was installing dapper from one of them discs you can get for free in the mail. As I got to the partioning part i choose the first option - "resize hda1 and use that space blablaa...", because I wanted to leave XP in there. I clicked forward and it started working so I figured "this will take a while", however when it was still in the exact same screen like two-three hours later I canceled the partioning and restarted the installation. So far all good, but it just wouldnt work so I started fiddeling with the manual partitioning and suddenly I can't see the windows partion any longer and windows wont start #-o

I figured out fdisk or cfdisk might be able to help me fix this as long as the drive hasnt been over-written (which I find hard to believe since nothing has been insalled), but how, what do I do???

Please dont mention backups... I know I should have done one :( (but honestly, who ever does??)


Thanks in advance Ubuntu Forums for saving my life...

---

### Post by Tomosaur on 2006-07-31
Ouch. Sounds like a pretty big problem you got there. Considering you cancelled the partitioning, it'll be pretty difficult to troubleshoot. It's possible your Windows partition has been resized and the partitioner moved on to setting up your linux filesystem, or maybe it was still in the middle of playing with your windows partition, in which case you'll have a much bigger problem.

In any case, you should probably sort your partitions out seperate from the installer. It crashed on me first time too, and I had to reinstall windows from scratch :/

I'm not too sure how to sort this problem for you, so just consider this a handy bump to stop it getting buried :)

Good luck.

---

### Post by catlett on 2006-07-31
Do you have an XP installation disk? If so recovery is easy. Most likely all that is lost is the mbr.
In case you have an XP install disk, boot into it.
You want to enter recovery mode. At the first prompt you have choices, select r. You will be taken through a couple of screens and eventually asked which installation of windows you want to use to run recovery.
You only have one so enter 1. Next it will ask for an administrator's password, everyone is an administrator on XP unless you made a user account. So enter your password. At the prompt enter```
 fixmbr
```It will give you a warning prompt but don't worry, your system is already unbootable :D 
That rewrites the mbr and you will be able to boot into windows (as long as it's there).
If you don't have an XP disk your next best thing is to boot to a linux live cd and look for your windows parttition.
Was the installation disk a live cd?

---

### Post by az on 2006-07-31
Boot the live cd again and use parted to see what your partition table looks like.  You can always start with a blak partition table and use parted to "rescue" lost partitions.  Your data is still there, just the partition table is not pointing to it.

From the command line, run
sudo parted /dev/hda (if that is the correct drive)

print

that will show you your partitions

if they are borked, you can delete all of them

rescue
it will prompt you for the start, enter 0 and then it will prompt you for the end, enter the end of your drive (parted will tell you the number of blocks when you start it.  When it finds a lost partition, it will ask you if you want it added to the partition table.  Say yes.

---

### Post by __a on 2006-07-31
Tomosaur: ok, thanks anyway :)

Catlett: Well I do not have an installation disc at the moment, but I'll just get hold of one and try that in the morning! But I am not really sure how the MBR can be ruined when my installation never got passed partitioning? isnt MBR where that GRUB-thing goes?
...and yes I have the new live CD with the installer on it.


one more thing: I got some output from fdisk, seems like hda1 has been made into a linux partion instead of ntfs (says so in the right-hand column:confused:). Also when i start the computer without CD it gives me an error saying something like "Operation system is corrupted" (dont know the exact english version, I have swedish), whatever this means

---

### Post by __a on 2006-07-31
> **azz said:**
> Boot the live cd again and use parted to see what your partition table looks like.  You can always start with a blak partition table and use parted to "rescue" lost partitions.  Your data is still there, just the partition table is not pointing to it.

From the command line, run
sudo parted /dev/hda (if that is the correct drive)

print

that will show you your partitions

if they are borked, you can delete all of them

rescue
it will prompt you for the start, enter 0 and then it will prompt you for the end, enter the end of your drive (parted will tell you the number of blocks when you start it.  When it finds a lost partition, it will ask you if you want it added to the partition table.  Say yes.


Hello azz! All went fine untill the "Say yes"-part, rescue didnt find any file system :(

I'll have to look in to it a bit better in the morning (its getting late on this side of the atlantic ;))

---

### Post by catlett on 2006-07-31
Right now the best option is to follow Azz's advice. It appears your partition has been changed and fixmbr won't work. So ask if you are not sure about Azz's advice and go for a recovery.
Before you panic too much, data can be recovered, Even when something is deledted it isn't gone. It has to be over written with something. Hopefully the partitioner started to change the partitiuon but didn't overwrite it or reformat.
Anyways go with Azz and also Google for the XP recovery console. It was a new feature in XP. I do not know all of it's capabilities.
[http://www.geocities.com/kilian0072002/recconsole1.html](http://www.geocities.com/kilian0072002/recconsole1.html)
It appears you can use it to access a system restore point but I don't know if a system restore can restore the filesystem. I thought it was more of a configuration restore type of thing.Good luck. Post tomorrow and hopefully more can be found. Azz is as smart as it gets so him being in the thread is to your benefit.

---

### Post by az on 2006-07-31
> **__a said:**
> Hello azz! All went fine untill the "Say yes"-part, rescue didnt find any file system :(

Crap!

If you reboot and run cfdisk from the live cd, does it show any leftover partitions?  If so, make cfdisk write a blank partition table and then reboot and try to rescue again.

If it fails again, you are screwed.

You can keep trying (out of superstition) or perhaps the reason why it failed in the first place was an intermittent hardware problem (that's all I got for you...)


If you have another disk of equal size or greater, you can use foremost to try to recover intact files from your drive.

[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

Use the most recent version from source, the one in the repos is too old.

[http://ubuntuforums.org/showthread.php?t=204306](http://ubuntuforums.org/showthread.php?t=204306)

---

### Post by __a on 2006-08-01
> **azz said:**
> Crap!

If you reboot and run cfdisk from the live cd, does it show any leftover partitions?  If so, make cfdisk write a blank partition table and then reboot and try to rescue again.

If it fails again, you are screwed.

You can keep trying (out of superstition) or perhaps the reason why it failed in the first place was an intermittent hardware problem (that's all I got for you...)


If you have another disk of equal size or greater, you can use foremost to try to recover intact files from your drive.

[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

Use the most recent version from source, the one in the repos is too old.

[http://ubuntuforums.org/showthread.php?t=204306](http://ubuntuforums.org/showthread.php?t=204306)


Since I removed all partions from the table in parted the last time around cfdisk only shows a large empty space.. Tried running parted recover again, but with the same result :(

I guess I'll go with foremost from here and just try to rescue as much data as possible.. Thanks for helping me out this far!

Edit: I just remembered reading somewhere last night that adding a new partion with the same size or larger to the partion table might save me, but I can't figure out how to make a new partion that is NTFS!? It just shows up as Linux :confused:?? Anyone got a hint?

---

### Post by H.E. Pennypacker on 2006-08-03
I don't mean to be a pain or anything and cause frustration, but this is a good example of why everyone should proceed safely and read the documentation that has been provided to them prior to doing anything major.  

Again, this is not a reference to any specific person, but instead a call for the need to be extremely cautious when doing something important as this.  Working with partitions is probably the most critical thing a computer user can do.  Most problems have solutions, including partitioning problems, but partitioning problems generally are far more dangerous.

You could tear X settings to pieces, and you could still get things back to normal.

---

### Post by __a on 2006-08-06
Problem solved! I put the harddrive as slave in my other XP box and  managed to recover the whole partion using [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")!!! After fixing the partion table and restoring the MBR I just put the drive back in its computer and booted right back into the old installation ^^

---

### Post by catlett on 2006-08-06
Great. Thank you for posting the end result and for the link to TestDisk. I never heard of it but thanks to you I do now. I'll definately be posting the link for people. (OSS to the rescue again)
```
 Summary

TestDisk queries the BIOS or the OS in order to find the Hard Disks and their characteristics ( LBA size and CHS geometry). TestDisk does a quick check of your disk's structure and compares it with your Partition Table for entry errors. If the Partition Table has entry errors, TestDisk can repair them. If you have missing partitions or a completely empty Partition Table, TestDisk can search for partitions and create a new Table or even a new MBR if necessary.

However, it's up to the user to look over the list of possible partitions found by TestDisk and to select the one(s) which were being used just before the drive failed to boot or the partition(s) were lost. In some cases, especially after initiating a detailed search for lost partitions, TestDisk may show partition data which is simply from the remnants of a partition that had been deleted and overwritten long ago.

TestDisk has features for both novices and experts. For those who know little or nothing about data recovery techniques, TestDisk can be used to collect detailed information about a non-booting drive which can then be sent to a tech for further analysis. Those more familiar with such procedures should find TestDisk a handy tool in performing onsite recovery.
```
Plus it supports just about every OS and filesystem
 Filesystems

```
TestDisk can find lost partitions for all of these file systems:

    * BeFS ( BeOS )
    * BSD disklabel ( FreeBSD/OpenBSD/NetBSD )
    * CramFS, Compressed File System
    * DOS/Windows FAT12, FAT16 and FAT32
    * HFS and HFS+, Hierarchical File System
    * JFS, IBM's Journaled File System
    * Linux Ext2 and Ext3
    * Linux Raid
          o RAID 1: mirroring
          o RAID 4: striped array with parity device
          o RAID 5: striped array with distributed parity information
          o RAID 6: striped array with distributed dual redundancy information 
    * Linux Swap (versions 1 and 2)
    * LVM and LVM2, Linux Logical Volume Manager
    * Mac partition map
    * Novell Storage Services NSS
    * NTFS ( Windows NT/2K/XP/2003 )
    * ReiserFS 3.5, 3.6 and 4
    * Sun Solaris i386 disklabel
    * Unix File System UFS and UFS2 (Sun/BSD/...)
    * XFS, SGI's Journaled File System 
```

---

