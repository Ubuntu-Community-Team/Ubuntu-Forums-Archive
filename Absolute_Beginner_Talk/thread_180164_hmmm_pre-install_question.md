---
title: "hmmm pre-install question"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by sotonin on 2006-05-21
I am really wanting to start using ubuntu but one of my biggest concerns is being able to use my existing hardrives to pull files off / store files on within ubuntu. They are all currently formatted with the NTFS file system and contain all manner of files from avi videos, mp3s to games and other data. Mainly they are iso images and archives. 

Can i still use these drives without having to wipe them out before hand?

(As secondary drives... i plan on nuking out my primary drive and letting ubuntu have at it with partitions.)

Also, should i try out the dapper or go with the older official release? I heard theres a lot of things about dapper that make upgrading later more of a pain than to just install fresh with dapper.

thanks!

---

### Post by Fass on 2006-05-21
You can't run Ubuntu off the NTFS drives, but you don't have to wipe them. Linux can read from NTFS partitions, so you'll still be able to access the files, if not edit them, unfortunately (there are ways of writing to NTFS in Linux, but they're a bit tricky to set up).

Oh, and go with Dapper. This close to final launch, there is no reason to install Breezy.

---

### Post by K.Mandla on 2006-05-21
Hi. You'll be able to read those drives without difficulty, but writing to them will be trickier. As I understand it, Ubuntu is set up to read NTFS without much trouble, but writing to NTFS is a no-no.

If you want both read and write capability, you'll want to look into FAT32 file format. Search the forums for "mount windows" and you'll find hundreds of posts explaining how to do that.

As far as upgrading, I'd go with Dapper, rather than upgrading from Breezy. I don't think it's any more difficult or error-prone to go from Breezy to Dapper, but it would be an added step. So long as you're installing Ubuntu, you might as well start with the most current version, and not end up re-downloading the entire business.

Good luck! :mrgreen:

---

### Post by oscar on 2006-05-21
As Fass said you should have no problems reading the files from your other hard drives once you have installed ubuntu. Writing to ntfs is still considered experimental as far as I am aware; so ntfs partitions are mounted read only by default.
The main thing you have to make sure of is that you install ubuntu to the correct hard drive, and do not accidenally wipe any files you want to keep, installing ubuntu over them. As these files are on different disks it should pose no problem.
As for which to install I personally would recommend dapper, it is so close to release that although it is still getting updated it is stable and I have never experienced any bad crashes.

[edit]K.Mandla, I doubt he will want to reformat his ntfs drives as they contain data he wants to keep, it is possible to write to ntfs (though it is still experimental), I do it with my dual boot windows partition (though very rarely) through ntfs fuse, there is a good howto here: [http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481)[/edit]

---

### Post by kostkon on 2006-05-21
[QUOTE=sotonin]They are all currently formatted with the NTFS file system and contain all manner of files from avi videos, mp3s to games and other data. Mainly they are iso images and archives. 

Can i still use these drives without having to wipe them out before hand?

(As secondary drives... i plan on nuking out my primary drive and letting ubuntu have at it with partitions.)
[/QUOTE]

Yeah, as said, it's not safe to write within Ubuntu to a NTFS partition. To transform your NTFS partitions to FAT32 ones would be the best option.

[QUOTE=sotonin]
Also, should i try out the dapper or go with the older official release? I heard theres a lot of things about dapper that make upgrading later more of a pain than to just install fresh with dapper.
[/QUOTE]

I recommend you to wait for the release of Dapper; do not install now Breezy neither the beta version of Dapper; only 10 days are left for the official release of Dapper!!

---

### Post by user1397 on 2006-05-21
and make sure to try out the dapper live cd ***first***, as soon as it comes out on June 1st, before installing it, to make sure your hardware is compatible.

---

### Post by sotonin on 2006-05-21
thanks for all the helpful responses!! i have a feeling the ubuntu community will be a great thing to be a part of. 

To clarify things, would i be able to take files from the read-only ntfs drives and copy them over to a fat32 partition, then from within ubuntu reformat that ntfs partition to fat32 and put the files back into place? so essentially transforming all my ntfs into usuable fat32 partitions?

thanks again!

---

### Post by Mustard on 2006-05-21
[QUOTE=sotonin]thanks for all the helpful responses!! i have a feeling the ubuntu community will be a great thing to be a part of. 

To clarify things, would i be able to take files from the read-only ntfs drives and copy them over to a fat32 partition, then from within ubuntu reformat that ntfs partition to fat32 and put the files back into place? so essentially transforming all my ntfs into usuable fat32 partitions?

thanks again![/QUOTE]
That sounds like a working solution, yes. :)

You are probably going to need to learn a few things about installing software via Synaptic or using apt-get from the command line before you can install the *gparted* application, which is a gui partitioning tool, so try to go through the basics of learning about installing software prior to launching yourself into the task of moving all these files around and formatting your ntfs partition.  You can find a Starters guide in the help menu of your chosen Ubuntu version.

---

### Post by mlind on 2006-05-21
you can use ext2 as for shared filesystem type too
see [http://www.fs-driver.org/](http://www.fs-driver.org/)

windows using ext2, now that how it should be ;)

---

### Post by sotonin on 2006-05-21
interesting... whats the better filesystem to use? Which is more reliable and standard, fat32 or ext2 ?

---

### Post by aysiu on 2006-05-21
[QUOTE=sotonin]interesting... whats the better filesystem to use? Which is more reliable and standard, fat32 or ext2 ?[/QUOTE] Ext3 beats FAT32, hands-down, especially if you use [http://www.fs-driver.org](http://www.fs-driver.org) to read/write Ext3 from Windows.

---

### Post by mlind on 2006-05-21
[QUOTE=aysiu]Ext3 beats FAT32, hands-down, especially if you use [http://www.fs-driver.org](http://www.fs-driver.org) to read/write Ext3 from Windows.[/QUOTE]

my words exactly. :mrgreen:

---

