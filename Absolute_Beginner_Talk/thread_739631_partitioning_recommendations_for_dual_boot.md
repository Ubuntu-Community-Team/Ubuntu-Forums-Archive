---
title: "partitioning recommendations for dual boot"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by ryancpratt on 2008-03-29
This summer I plan on upgrading my 5400rmp 120gig HDD to a 7200rmp 200gig HDD (unless a larger one becomes available by then for my dell e1505). I currently dual boot with Vista and Ubuntu. I use Ubuntu a lot more than Vista, so I plan on giving Ubuntu more space on the Harddrive. I would Like to do something similar to this which I found at [http://ubuntuforums.org/showthread.php?t=520960:](http://ubuntuforums.org/showthread.php?t=520960:)

partition 1: 8 GB, ext3, Ubuntu Feisty root (/)
partition 2: 20 GB, NTFS, Windows XP
partition 3: 8 GB, ext3, spare root partition for other linux distro.
------------------------
partition 4: Extended partition (the rest of the hard drive)
partition 5: 1 GB, linux swap (can be shared by both linux OS)
partition 6: 2 GB, FAT32, for transferring files between linux and windows.
partition 7: what remains of partition 4 after 5 & 6, Ubuntu Feisty home directory (/home)

but I will probably use 15 gigs for root (/), 60 gigs for Vista. I will not use the partition 3 referred to above. I'm not sure what the extended partition is for, so I will probably just give the extra space to the /home partition. I will use a 100 gig FAT32 partition for sharing between Vista and Ubuntu. So in the end it will look more like this:

partition 1: 15 GB, ext3, Ubuntu Gutsy (I guess I will upgrade to Hardy by then) root (/)
partition 2: 60 GB, NTFS, Windows Vista
partition 3: 4 GB, linux swap (I have 2 gigs of ram and want to play it safe)
----------------------------
partition 4: 100 GB, FAT32 (for a My Documents folder that I can share between both OS's)
partition 5: whatever is left can be my Ubuntu /home directory


Does this sound like a good plan?
Any recommendations?
In what order do I need to install my OS's (Ubuntu or Vista first?)?
What program should I use for partitioning?
How do I choose which partition does what (since I want them in that order)?
Is there a way to back up my Ubuntu partition so that I don't have to reinstall drivers all over again?

Any additional input would be appreciated!

Thanks,
Ryan

---

### Post by scragar on 2008-03-29
install vista first if you can, this stops vista taking a strange drive name and destroying your grub install.

The liveCd comes with gparted which is handy for editing partitions easily. if not you can install it just as easily:
```
sudo apt-get install gparted
```



it's proberly easier to teach windows to read ext3 partitions or ubuntu to read ntfs over making a new partition just for sending files between the two.

---

### Post by forrestcupp on 2008-03-29
personally, if you have that much space, I'd give a lot more than 15 GB for root because any apps or games you install from the repos will go on that partition.  If you start installing a lot of things, 15 GB can get eaten up quick.

---

### Post by ryancpratt on 2008-03-30
Points taken! Okay, I thought that sharing a FAT32 partition was something that linux and windows both agreed with? And I have no problem giving more space to the /root partition. How about the other questions?

---

### Post by scragar on 2008-03-30
my point, was that fat is a bloated and old partition type, if your going to have a folder just for your home directory then you are proberly just better of having windows be able to read and write to/from your home directory as a second drive, far easier in the long run(no worries about space limits or time taken to copy/move the files).

> How do I choose which partition does what (since I want them in that order)?
theres a realistic limit on the number of primary partitions, so your gonna have to split into several partitions within partitions(like how swap is by default, a swap partition inside a ext3 partition)
> Is there a way to back up my Ubuntu partition so that I don't have to reinstall drivers all over again?[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)
or
[http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37](http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37)

will let you make a liveCD of your current install, perfect for installing a copy of it later if you manage to break anything.

---

### Post by rkd on 2008-03-30
The disk format limits you to four standard partitions or three standard partitions and one extended partition.  You can create a lot (I don't know the limit) of partitions within the extended partition, so the limit of four standard partitions really isn't much of a restriction as long as you know to set up and use an extended partition.  So I'd say your layout should be:

I second scragar's advice to put the Vista partition first.  That's the arrangement that is most common and so has been tested the best.  You will be less likely to have weird problems if you stick with the conventional order.  Install Vista first, tell it not to use the whole disk, but just the amount you decide you are going to give it.  Don't try to change the size of a Vista partition with Linux tools -- I've seen reports of that either not working or causing problems.

Ubuntu can now read and write NTFS partitions, so you might want to change that FAT32 to NTFS.

So your layout perhaps could be:

1 Vista
2 Ubuntu
3 swap
4 extended partition (rest of drive)
5 My Documents (inside partition 4)
6 /home (inside partition 4)

But since Ubuntu can read and write NTFS, there might not be much reason to have the My Documents partition be separate from the Vista partition.

There are some advantages to having /home separate from the rest of the Ubuntu filesystem, but it isn't essential to do so.  If you moved /home back into the Ubuntu partition, you could get away with just three partitions: Vista, Ubuntu, and swap.  I think it is purely a personal preference whether you keep My Documents and /home as separate partitions or include them in the other partitions.

---

### Post by forrestcupp on 2008-03-30
I agree with rdk on a few points.  You should definitely use NTFS instead of FAT32.  Ubuntu has no problems with NTFS now.  I dual boot with Vista, and I don't have a separate 'shared' partition.  I just share files on my Vista partition.  That will save you a partition.

Also, like rdk said, I use Vistas Documents, Downloads, and especially Music folder from within Ubuntu, too.  It *is* wise to have a separate partition for /home that is ext3.

This is my setup, and I am pretty happy with it.

1. Vista - around 80 GB
2. Ubuntu root - around 60 GB
3. swap - I think 1.5 GB
4. /home - 40 GB

The only thing is that I'm not using Vista that much, so I may end up resizing to give more to Ubuntu.

---

### Post by hieronymouse on 2008-03-30
> **forrestcupp said:**
> 
2. Ubuntu root - around 60 GB

1. Why do you need so much room for Ubuntu root?
2. Would it be better to use The ["Ext2 Installable File System for Windows"]("http://www.fs-driver.org/") to enable Windows to read from the Ubuntu home partition, than to enable Ubuntu to read from NTFS (or use FAT)?  I found the above idea in the guide at [http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")
However, I think it was written before Linux could handle NTFS.  Lately I've noticed a problem in getting my Wine programs to write to my NTFS partition.  I didn't check why that is happening, but suspect that it has something to do with the file system type.
3. If the first part of the disk can be accessed more quickly, I guess it does seem logical to place the Ubuntu system directly after Windows, and the swap partition after that.

---

### Post by forrestcupp on 2008-03-30
> **hieronymouse said:**
> 1. Why do you need so much room for Ubuntu root?
2. Would it be better to use The ["Ext2 Installable File System for Windows"]("http://www.fs-driver.org/") to enable Windows to read from the Ubuntu home partition, than to enable Ubuntu to read from NTFS (or use FAT)?  I found the above idea in the guide at [http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")
However, I think it was written before Linux could handle NTFS.  Lately I've noticed a problem in getting my Wine programs to write to my NTFS partition.  I didn't check why that is happening, but suspect that it has something to do with the file system type.
3. If the first part of the disk can be accessed more quickly, I guess it does seem logical to place the Ubuntu system directly after Windows, and the swap partition after that.

1. Because I have the space, and almost every application or game you install goes somewhere on that partition.
2. It has been my experience that Linux does NTFS much better than Windows does ext3.  FAT is obsolete and out of the question except maybe for a small USB drive or something.

I would have given /home more space, but that partition is on its own hard drive, so that is impossible.  But because of my point #1, I definitely advocate giving plenty of space on the root partition.

---

### Post by scragar on 2008-03-30
even if linux does ntfs better than windows does ext3 it'd still recomend that you use ext3 instead of ntfs, the benifits of it far outweigh the negatives:

no need to defragment, ever
better permitions structure(even if you don't think you need it)
longer HD life by keeping files together to avoid seeking and long read or write times(ok, it's about 2 or 3% of the drives normal life, but it's still an advantage).

---

### Post by forrestcupp on 2008-03-30
The thing about my setup is that I am using my Vista partition to share files so I don't have to have a separate partition.  You can't install Vista on anything but NTFS, which Ubuntu handles very well.  So that's why I use NTFS.

Anyway, I've never found a working way that allows me to directly manipulate files on an ext3 drive from within Windows.  The only thing I've found that actually works like that only does up to ext2.  I had to use a program that reads files from an ext3 partition and copies them to my NTFS partition.  That's inefficient, so I'd rather just use NTFS which works well with both.  Also, even if you *can* make Windows directly read/write to an ext3 partition, permissions don't mean squat from Windows.  Anyone using Windows could access any file or directory even in the root filesystem and totally destroy it.  I don't want to give Windows that much unhindered power with my Linux filesystem.

But I'm almost always in Ubuntu nowadays, so it doesn't really matter anyway.

---

