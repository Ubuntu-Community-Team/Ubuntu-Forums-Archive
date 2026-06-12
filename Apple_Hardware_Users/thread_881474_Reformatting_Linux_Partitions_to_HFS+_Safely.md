---
title: "Reformatting Linux Partitions to HFS+ Safely?"
date: 2008-08-06
forum: Apple Hardware Users
---

### Post by dai_vernon on 2008-08-06
I installed Linux onto a partition on my G5 iMac several months ago to attempt to familiarize myself with Linux before getting a laptop.  I am now planning on reformatting these partitions to regain the 35 gigs of space they are taking up, as I do not use linux on this computer anymore.

I made 3 new partitions, a large main one, a swap, and a new world bootstrap.  If I simply reformat all of these to HFS, will I be able to mount them in OS X again?

Also, will removing Yaboot (the bootloader) just cause the computer to automatically boot into OS X?  Or is there another step I must take?  This is my main hangup to doing this now, because I have a feeling that it will be simply burning a live CD and reformatting the ext3, swap, and newworld partitions.

---

### Post by loboc on 2008-08-06
I thought OSX had a pretty good disk partitioning utility

If not look at gpartd you may have to run it off the live cd

---

### Post by dai_vernon on 2008-08-06
Well, this is tiger, and a PPC at that; I am unable to touch the non hfs partitions for some reason

---

### Post by tiresia on 2008-08-06
It looks like you have one HD, and that Ubuntu and MacOSX are on the same volume.
1. MacOSX can't read ext3 FileSystem
2. Apple Disk Utility does not change a partition, that is on the same volume where the OS is running.

So, if you want to dedicate the whole volume to MacOSX, you must start you iMac with the Installer-CD (Press C at booting). From there you can use Apple Utility Disk to reformat your HD.

**[COLOR="Red"]!!! ATTENTION: YOU WILL LOOSE ALL YOUR DATA (BOTH LINUX + MAC)!!! [/COLOR]**

Alternatively, if you have the Ubuntu-liveCD you can boot from it and use GParted (System > Administration > Partition Editor) to erase the three Ubuntu-Partitions and resize your MacOSX Partition. It should work well, anyway **[COLOR="Red"]make a backup of all your important files!!![/COLOR]**

---

### Post by dai_vernon on 2008-08-06
I wasn't planning on resizing my os x partition, just reformatting the linux ones and lumping them into one partition to use in os x as well (I believe the sectors are adjacent).  I realize that I'd be losing a bit of hd capacity with that, but I think it's ok; I'd rather not take the risk of resizing the partition.

Plus, I didn't even think that gparted could resize hfs partitions; I had to do it in parted in the CLI before.  Have the developers of gparted redone it so it can?

---

### Post by dai_vernon on 2008-08-06
GParted says that HFS partitions can only be a maximum of 2 GB.  Am I able to make a single HFS partition out of the 32.63 gigs of free space that now exist?

---

### Post by tiresia on 2008-08-06
In this link, you can see what gparted can do and what it can't
[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)
Yes, I was not precise. You can't grow a HFS+ Partition. 
You can shrink it - I meant this, but you can't grow it.
Anyway if you want just free space, you can delete your ext2, ext3, swap partitions, and use the new partition as unformatted in MacOSX.
Again, don't forget to make a backup of your important data!!!
Of course it is advisable, to format again the whole HD, as soon as you can.
MacOSX will appreciate it&#8230;:)

---

### Post by dai_vernon on 2008-08-06
I am in Disk Utility in OS X right now and am looking at my HD.  I have a 32.64 free space block, yet have no option to partition it.  The text on the right says

This disk contains the startup volume and can't be partitioned.

I have the free space selected and not the used space, how am I able to reformat this space?

---

### Post by tiresia on 2008-08-06
> **dai_vernon said:**
> how am I able to reformat this space?
As I wrote in a post before, you can't format a partition that is on the same volume (HD), where OSX is running.
If you want to use the Apple Disk Utility, you must start with your OSX Installer CD (Press C by starting).
But the Apple Disk Utility does not format just a partition. It will erase all your HD.:mad:
If you do not want to reinstall MacOSx, you could make an image of your MacOSx Partition, save it on an another Disk, reformat your Hard Disk and restore the old Image with Apple Disk Utility.:popcorn:
It worked always for me, but it is not always safe. 
If you do not have a lot of data, you can maybe just reinstall OSX.

Back up your data!!!

---

### Post by dai_vernon on 2008-08-06
I would really like to avoid having to reformat my whole thing, as that would be time consuming and very lame.  Is there any way, from a linux live CD, to make format that 32 and a half gigs of space to HFS so so I can make use of it in OS X?

Or, failing that, what other filesystem could I format that space to with a linux live CD so I could use it in OS X?  I have an mp3 player formatted in fat32 that I am able to mount and use in OS X, would this work as an option for that free space?

---

### Post by tiresia on 2008-08-06
Yes, if you start with your Ubuntu Live CD, you can erase all your Ubuntu-Partition and reformat the free-space with FAT32. MacOSX can read this FS. In a Fat32-formatted Partition you can't store files that are bigger than 4 GB.

---

### Post by dai_vernon on 2008-08-06
Hmm, it looks like OS X will not mount partitions on the boot device that are not HFS+.  This is very irritating.  Can you confirm that I can use parted to make a HFS+ partition larger?  I used parted when I shrank it, but can it increase size too?

---

### Post by dai_vernon on 2008-08-06
Ok, something is wrong.  When I load up parted in the hardy live cd it says that it has to access /dev/hda read only.  My disks identifier is /dev/sda, not /hda.

What is the matter?

---

### Post by cyberdork33 on 2008-08-06
don't use GNU tools to grow HFS+

delete the linux partitions to leave free space.

then in disk utility, select the free partition, and on the 'erase' portion of the utility you should be able to format the partition how you like. You do not have to "partition" because it is already partitioned. you just need to format the partition to HFS+. This will of course cause you to have two different HFS+ partitions, but at least the space will be usable.

a livecd called "parted magic" can create HFS+ volumes as well (jut still can't grow an existing partition).

---

### Post by dai_vernon on 2008-08-06
> **cyberdork33 said:**
> don't use GNU tools to grow HFS+

delete the linux partitions to leave free space.

then in disk utility, select the free partition, and on the 'erase' portion of the utility you should be able to format the partition how you like. You do not have to "partition" because it is already partitioned. you just need to format the partition to HFS+. This will of course cause you to have two different HFS+ partitions, but at least the space will be usable.

a livecd called "parted magic" can create HFS+ volumes as well (jut still can't grow an existing partition).


I don't think that Disk Utility will let me touch this free space.  All buttons and dropdowns in the erase tab are ghosted out for the free space (currently formatted as fat32).  When it was just plain free space it did not show up on the left side (where partitions show up).

I think this is so because it won't touch partitions on the disk on which the current boot is.  Is there a way I can HFS+ this extra space from within OS X?

---

### Post by cyberdork33 on 2008-08-06
> **dai_vernon said:**
> I don't think that Disk Utility will let me touch this free space.  All buttons and dropdowns in the erase tab are ghosted out for the free space (currently formatted as fat32).  When it was just plain free space it did not show up on the left side (where partitions show up). even booting the OSX disc? That is a bit suprising... If it is mounted, you will not be able to erase it.

---

### Post by tiresia on 2008-08-06
> **dai_vernon said:**
>  I think this is so because it won't touch partitions on the disk on which the current boot is.  Is there a way I can HFS+ this extra space from within OS X?

NO! There are some proprietary (not free!) software, that allow you to change the size or reformat one partition without destroying the whole volume. One of these is iPartition. Here you can download it.
[http://www.coriolis-systems.com/iPartition.php](http://www.coriolis-systems.com/iPartition.php)

Anyway you must start from another disk, you can't do it from inside the same volume.

---

### Post by tippyknit on 2008-08-15
> **dai_vernon said:**
> I would really like to avoid having to reformat my whole thing, as that would be time consuming and very lame.  Is there any way, from a linux live CD, to make format that 32 and a half gigs of space to HFS so so I can make use of it in OS X?

Or, failing that, what other filesystem could I format that space to with a linux live CD so I could use it in OS X?  I have an mp3 player formatted in fat32 that I am able to mount and use in OS X, would this work as an option for that free space?
Yes. I don't know whether this will work with a non-intel based mac, but what works for me is the following:
 1. Use the ubuntu live CD (gparted) to make the 32.5 gigs of free space into any format (other than swap)
 2. Use the macintosh CD (disk utility) and underneath something that should say your hard drive's capacity and some random information, you should see two different options. Select the one that isn't your macintosh hard drive, go to the format tab and chose mac os (extended, journaled) and click format.

The reason why this works is because gparted turns your volume into two seperate areas. Forgive me if this gets too complex, but one of them is either a 'ppc-based' or 'GUID' partition table and the other one is 'MBR' (master boot record). Apple doesn't know how to modify a ppc based or mbr partition table without formatting the whole volume, but gparted knows how to work with a mbr partition table. You can create a volume within that and then apple (at least in cases of intel-based macs) can format that volume, but not partition that. 

Alternatively, if you can live with FAT16 or FAT32, gparted can make that free space into either. I would format the free space into FAT 32, simply because if a non-intel based mac can't reformat that volume, FAT 32 is functional (until you need to move files with a size greater than 10 gigabytes, such as a one file that holds all of the lord of the rings trilogy.)

Tell me how that works!

---

