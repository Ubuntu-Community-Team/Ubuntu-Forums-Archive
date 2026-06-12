---
title: "Leopard, Vista, Hardy Triple Boot enquiry"
date: 2008-05-06
forum: Apple Hardware Users
---

### Post by c3007223 on 2008-05-06
Hello,

I have a macbook pro (santa rosa) with Leopard, Vista and Hardy installed. I recently upgraded from Gutsy and this has stopped Vista from loading (I should be able to find a solution to that on these forums for the short term). To the point, I want to re-partition my hard drive and re install the three os's, with a fourth partition that can be used to store files, music, programs, etc. My aim is to have all of these files readily accessible from each operating system, with minimal fuss - I am hoping to be able continue bit torrent downloads from one system that were started in another for example. Another example is to have the web browser in each system use the same book marks. This brings me to the following questions:

1. What file system is best to use in the fourth partition? (holding all of the common files, etc) This is something I have had difficulty finding an answer to.

2. I understand that the swap partition for linux is not necessary (I have 4 gb ram) - I want to be sure of this.

3. Can programs from different operating systems work harmoniously with common files (see the bit torrent and web browser examples above), or is this just a dream? If so are there any resources that must be read to successfully attain this?

Cheers,

Dan

---

### Post by cyberdork33 on 2008-05-06
> **c3007223 said:**
> Hello,

I have a macbook pro (santa rosa) with Leopard, Vista and Hardy installed. I recently upgraded from Gutsy and this has stopped Vista from loading (I should be able to find a solution to that on these forums for the short term). To the point, I want to re-partition my hard drive and re install the three os's, with a fourth partition that can be used to store files, music, programs, etc. My aim is to have all of these files readily accessible from each operating system, with minimal fuss - I am hoping to be able continue bit torrent downloads from one system that were started in another for example. Another example is to have the web browser in each system use the same book marks. This brings me to the following questions:

1. What file system is best to use in the fourth partition? (holding all of the common files, etc) This is something I have had difficulty finding an answer to.

2. I understand that the swap partition for linux is not necessary (I have 4 gb ram) - I want to be sure of this.

3. Can programs from different operating systems work harmoniously with common files (see the bit torrent and web browser examples above), or is this just a dream? If so are there any resources that must be read to successfully attain this?

Cheers,

Dan

I would guess your issue is realted to the partition table being out of sync. Try that first (in the rEFIt menu, choose the partition tool).


[LIST=1]
[*]FAT32. The problem here is that filesize is limited.
[*]swap is not "necessary" but it is good to include it. You can also use a swapfile if you rather.
[*]I don't see why you would have an issue. Firefox bookmarks are common across systems, and so are torrents.
[/LIST]

---

### Post by c3007223 on 2008-05-06
> **cyberdork33 said:**
> I would guess your issue is realted to the partition table being out of sync. Try that first (in the rEFIt menu, choose the partition tool).


[LIST=1]
[*]FAT32. The problem here is that filesize is limited.
[*]swap is not "necessary" but it is good to include it. You can also use a swapfile if you rather.
[*]I don't see why you would have an issue. Firefox bookmarks are common across systems, and so are torrents.
[/LIST]

Thanks for the reply,

Is there any other solution than FAT32?

Cheers

---

### Post by cyberdork33 on 2008-05-06
> **c3007223 said:**
> Is there any other solution than FAT32?
There are plenty of solutions other than FAT32, but you asked for the best one ;)

you can use NTFS, HFS+, ext2/3

each of these have some issues though. NTFS requires MacFUSE which is not currently developed. HFS+ has issues under linux. ext2/3 relies on drivers that are not developed to work with OSX.

Hands down, the most compatible filesystem out there is fat32.

---

### Post by billbear on 2008-05-06
Paragon's NTFS for Mac OS X seems to work very well. It is not free though.

---

### Post by c3007223 on 2008-05-07
Thanks guys.

I was mucking around last night and this morning and made a few discoveries.

1. I could get my linux drive to mount in os x using the dev program located here: [http://sourceforge.net/projects/ext2fsx](http://sourceforge.net/projects/ext2fsx)
and the instructions on this page: 

[http://fuz2y.blogspot.com/2008/04/how-to-mount-ext3-partition-on-os-x.html](http://fuz2y.blogspot.com/2008/04/how-to-mount-ext3-partition-on-os-x.html)

This required a bit of mucking around and I still could not get write priveliges to the ext3 partition from os x(though this may be due to the fact I was mounting the / ubuntu directory). From memory the drivers at 

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) 

should give me read and write to ext3 from windows. All of the mucking around with os x makes me think to avoid ext3 though.

2. I also came across this page

[http://en.wikipedia.org/wiki/File_system_comparison](http://en.wikipedia.org/wiki/File_system_comparison)

which backs up the comments that have already been made - FAT32, NTFS, ext2/3 are useable by all three operating systems (with various drivers). The interesting point though is that the NTFS-3g driver is free and supposedly provides stable, read/write support for Linux and OS X. I think I will try to make a few small partitions, each with a different file system to muck a round with for a while.

I will be happy in the end to use the FAT32 system as cyberdork33 has already suggested but before then, does NTFS-3g require MAC FUSE to work? Assuming that i can get NTFS or EXT3 supported across the board, are there any advantages in using one file system over another?

Thanks again,

Dan

EDIT: to clarify the last question, are there any real benefits from using NTFS for example over FAT32? I am not interested in specialist features that normal people will never need.

---

### Post by cyberdork33 on 2008-05-07
the filesize limitation is gone. I believe that the ntfs-3g driver requires FUSE, and thus this would be needed under OSX as well.

---

### Post by c3007223 on 2008-05-07
Ok, cool. Thankyou for the help guys. Due to work it will probably be the weekend before I can muck around with any of this stuff. FAT32 definately looks like the way to go then. I will let you know how I go.


Cheers,

Dan

---

### Post by c3007223 on 2008-05-12
Hello again,

I have a new problem now,

I have completely reformatted my HDD. I have installed the 3 operating systems, without a linux swap partition (I could not find how to use a swap file so I don't know if I am using one of those). All partitions work well. I also have made a FAT32 partition after all the others as well to share as I initially planned. The only problem is that Ubuntu Hardy is the only system that can mount the partition. The disk utility in os x will not let me erase, or reformat the volume. The best i get is the following error:

'Partition failed with the error:

MediaKit reports partition (map) too small.'

Anyone know how to knock this over?

Cheers,

Dan

---

### Post by Jammy4041 on 2008-05-12
I think that the 4th Partition will be an area which all Operating Systems on your computer can access. In which case, you will want to format it as FAT.

Windows and Linux can read and write to FAT. I'm positively sure Mac OS X can read and write to it as well. I would be suprised if it didn't.

---

### Post by cyberdork33 on 2008-05-12
> **c3007223 said:**
> Hello again,

I have a new problem now,

I have completely reformatted my HDD. I have installed the 3 operating systems, without a linux swap partition (I could not find how to use a swap file so I don't know if I am using one of those). All partitions work well. I also have made a FAT32 partition after all the others as well to share as I initially planned. The only problem is that Ubuntu Hardy is the only system that can mount the partition. The disk utility in os x will not let me erase, or reformat the volume. The best i get is the following error:

'Partition failed with the error:

MediaKit reports partition (map) too small.'

Anyone know how to knock this over?

Cheers,

Dan

I noticed that some people have problems seeing the FAT32 partition from OSX unless the partition was created with Disk Utility. I am not sure of the reason. Are your partition tables in sync?

---

### Post by c3007223 on 2008-05-12
Jammy 4041: I did format the drive as FAT32 for that reason. I did this from the Hardy intallation, as part of installing Hardy.

cyberdork33: After installing Hardy, I had the "no bootable device" error. Synchronising my partition tables in rEFIt solves this. OS X does throw the partition table out of sync every time I try to reformat the fourth partition from OS X disk utility though.  

More things that I learnt: When I deleted my 4th partition and reformatted as "no file system", Ubuntu couldn't mount it, but OS X recognised it as FAT (MSDOS) and mounted it. I even mucked around and could write to it. 

OS X has not been able to do anything to that partition (format or erase) even when it was "no file system" in Hardy (as above) - only being able to mount and write to it on that occasion. 

Vista has not been able to mount the partition or even recognise it as FAT32. This makes me think there is something wrong with the way Hardy is formatting the drive. Apparently I need to download a program for vista to format a partition my size (~100GB) as FAT32. I haven't downloaded this yet so dunno if this will fix the problem.

Good to see you guys are still interested,

Cheers

Dan

---

### Post by c3007223 on 2008-05-19
Hello again,

I got sick of trying to reformat the partition this way and that - I wiped that partition and the ubuntu partition as well (the one directly before that). I reinstalled ubuntu and labelled the fourth partition as 'no file system' during the installation. I then formatted the drive as FAT32 in OS X. This has worked. I have yet to try read/write in windows, but for now this solution seems satisfactory. 

I have one little question now - I cannot figure out how to rename my Ubuntu Hardy partition in OS X - all that will show up is 'UNTITILED'. I have installed the extfsx drivers by the way. This partition shows up as 'File System' in Hardy. Is there a way to rename the drive in Hardy and OS X? 

Cheers

Dan

---

### Post by cyberdork33 on 2008-05-19
> **c3007223 said:**
> I have one little question now - I cannot figure out how to rename my Ubuntu Hardy partition in OS X - all that will show up is 'UNTITILED'. I have installed the extfsx drivers by the way. This partition shows up as 'File System' in Hardy. Is there a way to rename the drive in Hardy and OS X?
That is one of the things that is stored in a .DS_Store file i believe. You might be able to create one manually on your Ubuntu partition, but I don't know if it will work.

---

