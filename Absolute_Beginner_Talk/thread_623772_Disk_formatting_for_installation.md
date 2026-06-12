---
title: "Disk formatting for installation"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Cams on 2007-11-26
I'm a complete n00b to Linux and have decided to dedicate an ageing P4 2.0 GHz to Ubuntu and see how I get on with it. At the moment I have two physical HDDs in the system. Both are formatted with NTFS and one has two partitions, one of which contained Windows XP. The second partition contains data that I would like to keep, as does the second physical drive. 

I've downloaded the latest ISO but wondered what prep work I should do on the drives first. Do I need to reformat the OS partition first, or does the install take care of that? And if I do need to do that, what file system should I format it with?

Also, will the data partition and data drive be visible by the OS? I'm guessing not. So what do I need to do to make them visible without losing the data? I have Partition Magic which I believe can be used to convert file systems without data loss. 

I'm looking forward to entering the Ubuntu world!

Thanks in advance
Cams

---

### Post by hyper_ch on 2007-11-26
As you seem familiar with partitioning in windows I'd recommend this approach:

(0) **MAKE A BACKUP FIRST!!!**

(1) Partition your disks the way you want. The total space you want to give to linux, leave that as unpartitioned! E.g. if you wand partition 2 of harddisk 2 be for linux, then unformat that one with a partitioner.

(2) Upon installation of linux, you'll be asked about the partitioning. Select there "use largest continouous empty space" or something similar (in meaning). Do NOT select "use entire disk".

(3) Go on and enjoy linux.


Instead of putting all into "one" partition, you could create a seperate home partition (the home partition is where your personal settings and files are, sort of like the "document and settigns" folder on your windows c:\ drive).

The parameters for manual partition with a seperate /home folder would be somethign like this:

- Partition one:
    size: double of your ram (max. about 2 GB); if you're on a notebook, make it at least as big as your ram if you want to use hibernate!
   filesystem:  SWAP
- Partition two:
   size: about 10 GB
   filesystem: EXT3
   Mountpoint:  "/" (root)
   Format: Yes
   Bootable: Yes
- Partition three:
   size: rest you want to spend on linux
   filesystem: EXT3
   Mountpoint: "/home"
   Bootable: No
   Format: Yes

Just make sure you select the unpartitioned space. It's not difficult if you can read and have some idea of how your partitions are already setup.

---

### Post by Harpoon on 2007-11-26
You don't say, but I am assuming that this is a desktop with two ide drives.  If that is correct, then you should probably
1) defrag the second hard drive in windows;
2) if you have partition magic, use that to shrink the partition on the second data drive, leaving enough room to install ubuntu.  You can get by with 10 gb, but you would probably want more depending upon the size of the drive and the room the data takes.

If you don't have partition magic, download the gparted live cd, burn it, boot into that and do as above.  Very easy to follow the instructions there.

3) once that is sorted out, leave the empty space on the drive as "unallocated" and boot into the ubuntu cd.
4) when you get to the part about partitions, tell it to use the largest available free space (that is the part that is unallocated);
5) wait a few minutes and enjoy your installation.

and yes, ubuntu will see the data on the ntfs partitions.

Good luck and bundles of fun.

---

### Post by forestpixie on 2007-11-26
I wouldn't change the file format of the partitions you've got data on - gutsy will read from ntfs - and write I believe without installing anything, feisty needed a rpgram

So if you are only going to be replacing xp with ubuntu you don't need to do anything - it will format as partt of the install.

---

### Post by Cams on 2007-11-26
Wow, thanks for all the help folks. It's much appreciated!

Yes, it's a desktop with two IDE drives. As I said, one drive has two partitions - one of 20 gigs and one of 100. I was going to install Ubuntu in the 20-gig partition. The other drive is not partitioned and is purely used for data. 

@hyper_ch

Is there an advantage to having separate partitions for swap, root and home? Does it give a performance boost to have it set up that way or is it more secure? Does Ubuntu allow for these parameters during installation? What I would do in that case is delete the NTFS 20-gig partition and leave it unpartitioned, then boot into the Ubuntu installer and from there create the swap, root and home partitions? And then I could use the remaining NTFS partition and the other physical drive (also NTFS) for data?

Everything is already backed up. In fact, the PC in question actually IS the backup!

I'm really looking forward to this and hope that it's not too troublesome. I do have PM8 so I can use that for partition management. 

Cheers
Cams

---

### Post by fineas on 2007-11-26
> **Cams said:**
> 

Is there an advantage to having separate partitions for swap, root and home? Does it give a performance boost to have it set up that way or is it more secure? Does Ubuntu allow for these parameters during installation? What I would do in that case is delete the NTFS 20-gig partition and leave it unpartitioned, then boot into the Ubuntu installer and from there create the swap, root and home partitions? And then I could use the remaining NTFS partition and the other physical drive (also NTFS) for data?



First, you ought to have a separate swap partition.Neither it gives a performance boost, nor it is more secure; you just have to. Separate home partition isn't obigatory, but it's a good thing.And yes, ubuntu allow for these parameters during installation, as long as you follow manual installation. Finally, you wiil use the remaining NTFS partition and the other physical drive (also NTFS) for data. 
Check this: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) and some other stuff in that site (note:Ubuntu can natively write and read to NTFS)

Things seems to be easier than you (may) think

Best wishes

---

### Post by hyper_ch on 2007-11-26
Well, the reason to have a seperate hoe partition is really good:

In /home you will save all your user settings for different programs (e.g. email accounts, instant messenger, browser bookmarks, ....)

So, if you want to reainstall your system again, you will NOT format the /home folder but simply mount it during the install process. So all your files stay intact ;)

---

### Post by Cams on 2007-11-27
Thank you once again for your help. It makes me feel quite comfortable venturing into Ubuntu knowing that these forums are so helpful!

I installed it this morning doing the three partition method manually and it really wasn't that hard! It sees all of the NTFS partitions and has no trouble reading from them. I'm testing Sound Juicer right now and tested Totem Movie Player as well. Both work well! Open Office seems very capable too and I think that Ubuntu is perfect for this computer! If fact, it's actually easier to use for a die-hard Windows user than OS X. I just got an iMac last week and Ubuntu is easier to use from the perspective of a Windows user. I'll stick with all three though (OS X, XP and Ubuntu) and broaden my horizons. 

Thank you once again, 

A new Ubuntu user!

---

