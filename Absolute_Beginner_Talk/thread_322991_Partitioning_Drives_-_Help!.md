---
title: "Partitioning Drives - Help!"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by Blue_Sky on 2006-12-21
Hi,
I decided that I would experiment with Ubuntu linux while I’m home for the holiday season, but I’ve run into what seems to be an insurmountable problem. I’d like to run Ubuntu on my laptop, but I can’t afford to reformat the hard drive to partition it, as I don’t have any of the Windows reinstallation cd’s with me. XP is a necessary evil, as most of the programs I require for school don’t have linux or Mac equivalents. Is there any way to partition my hard drive without reformatting it? And what file system does Ubuntu (/linux in general?) use, as opposed to NFTS or FAT32, and how would I go about changing that new partition to the required file system?
Any help would be greatly appreciated.

Blue

---

### Post by kidders on 2006-12-21
Hi there,

Any partition resizer will do the job for you ... The Ubuntu installer has its own if you don't already have one. Just be sure and defragment your existing filesystems first.

Linux is happy enough with almost any filesystem, but it does prefer to use one with good support for permissions & file ownership, like Ext3, ReiserFS, etc.

---

### Post by SupRspi on 2006-12-21
Ubuntu will by default want to use ext3 and a swap partition.  Common information I've been givin (yes, I'm very new to linux) is to have your swap partition 1 to 1.5 times the size of your physical ram.

If you boot off the live CD and do the install you can go through the steps and see how things work out - the install seems to be pretty easy from the 8 or so times I've done it, even the gparted partition manager it loads if you want to do your partitioning yourself.

Ubuntu has options for installing into the largest contiguous free space, resizing your windows partition, erasing your windows partition and editing your partitions yourself.

In your case, I would edit the partition myself and resize the main partition to allow for some free space - swap up to 1GB (seems a little big) Ext3 for the root partition (known as /) and if you want to swap files back to XP a Fat32 partition if your main partition is NTFS.  So at the end it would look like this:

NTFS <---WinXP (Leave enough free space to use normally)
Ext3 <---- / of Ubuntu (min 2GB)
Swap
Fat32 <--- If your WinXP partition is NTFS, otherwise just make a folder and write to it to transfer files if your XP is already on a Fat32 partition.

Hope this helps!

---

### Post by steve.horsley on 2006-12-21
One of the options in the Ubuntu installer is to resize the NTFS partition to make room for more partitions. If you don't want trust Ubuntu to do this, you could use something like Partition Magic to do the same thing - shrink the NTFS partition and leave the rest of the disk space unallocated/unpartitioned and then tell the Ubuntu installer to use the free space.

Whichever way you do it, make a backup of your data first, and realiese that there is always a small possibility of something going wrong and scrambling windows. 

Ubuntu will install two partitions in the free space - an ext3 partition for the system and a smallish swap partition for virtual memory. You really need a minimun of 3G free space, and 10 would be nice.

---

### Post by Blue_Sky on 2006-12-21
Thanks guys, thats really helped. 
Now I have a few more questions. What is a swap partition and what dictates how large it has to be (I have 2 GB of RAM)?
Does Ubuntu install with a program that will let me choose which OS to use at startup, or will I need to install one myself?

Thanks,
Blue

---

### Post by Bachstelze on 2006-12-21
Swap space is the Linux equivalent to Windows' Virtual Memory. If you have 2 GiB of RAM, you don't really need it. Creat 128 or 256 MiB of it just to be sure but it won't be used ofte.

And yes, Ubuntu installs GRUB, which is a boot loader and will let you choose at boot-time wich OS you want to run.

---

### Post by rsambuca on 2006-12-21
If you have 2GB of Ram, you probably don't even need a swap!

btw, how big is your hard drive?  We might be able to offer suggestions as to sizes of partitions if we knew.

---

### Post by Blue_Sky on 2006-12-21
Thanks everyone.
I'm quite impressed by the speed and helpfulness of the replies.

Blue

---

### Post by anaconda on 2006-12-21
> **Blue_Sky said:**
> Thanks guys, thats really helped. 
Now I have a few more questions. What is a swap partition and what dictates how large it has to be (I have 2 GB of RAM)?
Does Ubuntu install with a program that will let me choose which OS to use at startup, or will I need to install one myself?

Thanks,
Blue

With a laptop swap can be handy, because hibernate needs swap, and you have to have more swap than ram if you want  to use hibernate.

---

