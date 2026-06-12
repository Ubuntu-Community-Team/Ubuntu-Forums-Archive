---
title: "Partitioning Dell Windows XP to dual boot w/Ubuntu"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by bigwoo6 on 2008-01-12
My current partitions:

DELLUTILITY(*:)      FAT        54.9MB
Local Disk (C:)         NTFS       235,187.1MB
Local Disk (*:)         CP/M,Concurrent DOS, CTOS     3,176.9MB
(*)                          Unallocated                    7.8MB

I'm confused as to how to repartition to give it space to run the linux OS and swap partition without messing up anything in my windows environment.  Any guidance would be greatly appreciated.....

Thanks in advance - 

SuperN00b

---

### Post by Paqman on 2008-01-12
First of all, back up any important data on your windows partition. Then defrag it thoroughly. Auslogics make an excellent free defrag tool that will do this a lot quicker than the default windows one.

Then you'll want to shrink that partition down a bit. About 20Gb of free space should be plenty, although you can make it as big as you like.

Then make a new partition from the space you just created and choose swap as a the file system. It needs to be about twice the size of your RAM, up to a max of about 1GB. Then select the rest of the unallocated space and format it as ext3 (the most common Linux filesystem)

The Ubuntu installer can do the partitioning for you during installation, or you can use Gparted when you're running from the LiveCD before installing.

---

### Post by fiddledd on 2008-01-12
here is an old, but fairly complete guide:

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

there are many others as well. 
I imaged my hard drive (True Image or Clonezilla or Partimage), 
Backed up up ALL my important data to external drives, 
Defragmented the partition I was going to clain some space from,
Used Gparted (from Ubuntu LiveCD) to resized a partition (leaving 30gb unallocated space)
Then clicked Install from the Desktop and let the installer do the rest.

Sorry but I think I've basically given you a cut down version of the link info I poasted :)

EDIT:
yet again I posted too late, sorry :(

---

