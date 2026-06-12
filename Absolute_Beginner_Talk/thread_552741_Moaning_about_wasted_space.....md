---
title: "Moaning about wasted space...."
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-09-16
I am totally amazed by how much space formatting wastes.  For example I have a 500GB drive.  After formatting to ext3 I end up with 435GB.  It seems that the format leaves 459GB and something else very hidden and system related takes the balance.  So 65GB is gone for what.

This is df -h
/dev/sdd1             459G  426G  9.5G  98% /media/disk

So here I have used 426GB and have 9.5GB free space = 435GB

It was suggested that I could run the following command and recover some of the space
sudo tune2fs -m 0 /dev/drive name
but I get the error “Could not find valid file system  superblock”.

Any suggestions of what I can do to reclaim some space since loosing such a lot of space for no gain makes storage quite expensive?  Perhaps I should use FAT32 ....

---

### Post by CaptainInsaneO on 2007-09-16
I don't want this to sound rude, but think about how the hdd manufacturers are counting 1mb as 1000kB, and it's actually 1024... that's where the difference comes from.

---

### Post by Bachstelze on 2007-09-16
> **CaptainInsaneO said:**
> I don't want this to sound rude, but think about how the hdd manufacturers are counting 1mb as 1000kB, and it's actually 1024... that's where the difference comes from.

Not only. ext2/3 formatting by default reserves 5% of the filesystem size for use by the superuser :

[quote=man tune2fs]       -m reserved-blocks-percentage
              Set the percentage of the filesystem which may only be allocated
              by privileged processes.   Reserving some number  of  filesystem
              blocks for use by privileged processes is done to avoid filesys-
              tem fragmentation, and to allow system  daemons,  such  as  sys-
              logd(8),  to continue to function correctly after non-privileged
              processes are prevented from writing to  the  filesystem.   Nor-
              mally, the default percentage of reserved blocks is 5%.[/quote]

Setting it to 0 is a bad idea. Rather, do :

```
sudo tune2fs -m 1 /dev/sdd1
```

---

### Post by K.Mandla on 2007-09-16
CaptainInsaneO is probably right. I think what you're seeing is the Mebibyte/Megabyte difference in drive size.

[http://en.wikipedia.org/wiki/Megabyte](http://en.wikipedia.org/wiki/Megabyte)
[http://en.wikipedia.org/wiki/Mebibyte](http://en.wikipedia.org/wiki/Mebibyte)

I don't think there's any storage space lost by formatting. It's just a different calculation of drive size.

---

### Post by Bachstelze on 2007-09-16
> **K.Mandla said:**
> 
I don't think there's any storage space lost by formatting. It's just a different calculation of drive size.

Yes, there is, it's the difference between the 459G and the 426G + 9G :

```
firas@Ana ~ $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6              75G   58G   16G  79% /data
firas@Ana ~ $ sudo tune2fs -m 1 /dev/hda6
tune2fs 1.40.2 (12-Jul-2007)
Setting reserved blocks percentage to 1% (198241 blocks)
firas@Ana ~ $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6              75G   58G   17G  78% /data

```

The difference is minimal on my 75G partition but that's where the 23G are gone (5% of 459).

---

### Post by K.Mandla on 2007-09-16
Oops, my fault.

---

### Post by Bachstelze on 2007-09-16
> **K.Mandla said:**
> Oops, my fault.

You were right too, the difference in disk size measurement is the one between the 500G that's written on the drive and the 459G total size reported by df ;)

```
firas@Ana ~ $ echo $((500000000000/(1024*1024*1024)))
465
```

with the additional overhead due to cylinder sizes, MBR, partition table, superblocks and so on.

---

### Post by expatCM on 2007-09-16
Well using binary interpretation of 1,048,576 to represent 1,000,000, a 500GB drive becomes a 476.80GB drive.  Quite why the trading standards departments do not prosecute the hard drive companies for this fraud is something I do not understand.

However, 476.8GB to 435GB is a difference of 42GB which is a huge amount for a FAT and the reserved file system space for the super user.  We know that the reserved space is 5% (of what, presumably the volume after format).

Wikipedia shows that the FAT is not too efficient, for example two copies of the file allocation table and clusters being allocated irrespective of use.

> A FAT file system is composed of four different sections.
1.The Reserved sectors, located at the very beginning. The first reserved sector is the Boot Sector (aka Partition Boot Record). It includes an area called the BIOS Parameter Block (with some basic file system information, in particular its type, and pointers to the location of the other sections) and usually contains the operating system's boot loader code. The total count of reserved sectors is indicated by a field inside the Boot Sector. Important information from the Boot Sector is accessible through an operating system structure called the Drive Parameter Block in DOS and OS/2. For FAT32 file systems, the reserved sectors include a Backup Boot Sector at Sector 6. 
2.The FAT Region. This contains two copies of the File Allocation Table for the sake of redundancy, although the extra copy is rarely used, even by disk repair utilities. These are maps of the Data Region, indicating which clusters are used by files and directories. 
3.The Root Directory Region. This is a Directory Table that stores information about the files and directories located in the root directory. It is only used with FAT12 and FAT16 and means that the root directory has a fixed maximum size which is pre-allocated at creation of this volume. FAT32 stores the root directory in the Data Region along with files and other directories instead, allowing it to grow without such a restraint. 
4.The Data Region. This is where the actual file and directory data is stored and takes up most of the partition. The size of files and subdirectories can be increased arbitrarily (as long as there are free clusters) by simply adding more links to the file's chain in the FAT. Note however, that clusters are allocated in their entirety, and so if a 1 KB file resides in a 32 KB cluster, 31 KB are wasted.

The reason I am prompted to raise this question is that I just changed a 500GB drive from FAT32 to ext3.  The trouble is that the data that was on there will no longer go back since there is insufficient space.  Since the data came off the drive it can only be the ext3 file system which is the problem ........

---

### Post by Bachstelze on 2007-09-16
What are you complaining about ? ext3 is much more performant and reliable than FAT, but this comes at a cost. If you can't afford it, feel free to stay with FAT.

---

### Post by expatCM on 2007-09-16
df -h before and after running sudo tune2fs -m 1 /dev/sdd1

/dev/sdd1             459G  426G  9.5G  98% /media/disk
/dev/sdd1             459G  426G   29G  94% /media/disk

So a nice saving :)

---

### Post by expatCM on 2007-09-16
HymnToLife, what I am complaining about is converting to what you are saying is a better file system and finding out that it is only better with a price.  The price is less storage.   

I am a user, I do not know how to measure that ext3 is better than FAT32 but I do know how to measure space, space is a function of money and even though I have about 3TB of storage there never is enough and I am always short.  

But if I start to work things out it seems that I get cheated by the hdd manufacturers on dishonest product description, I loose on inefficiencies in the FAT and I also look on the quirks of one file system compared with another.  Due to these inefficiencies, on 3TB of storage, I am paying for quite a lot of what I have no hope of ever using.

That is what I am complaining about.

Hope you understand :)

---

### Post by CaptainInsaneO on 2007-09-16
I most definitely agree with you on the point you made about manufacturers being dishonest. It's driven me nuts for YEARS. :mad:

---

### Post by zero244 on 2007-09-17
I agree it is dishonest the way manufacturers overstate the drive size. I factor that in when I buy a drive. I expect to lose at least 10 percent of my drive space with formatting.
One thing about Linux the OS overall uses far less space than XP and certainly Vista.
If you have plenty of space why worry what you dont have.
Most people who have bought drives over the years dont expect a 500 gig to have 500 gigs.
I can remember when hard drives cost a dollar per MEG.......now you can get them for less than a dollar per GIG.

---

