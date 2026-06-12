---
title: "Need to enlarge my XP partition."
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by henthorn on 2007-06-23
I didn't realize that I was still going to be so dependent on XP for so many things when I installed Ubuntu, so I only allowed 10GB for XP.  I need a lot more.  I downloaded gparted thinking it would allow me to resize the XP partition to a much larger size. Didn't happen.  I shrunk the 137gb of the Ubuntu partition to 70gb and all that did was give me about the same amount of un-allocated space between the Ubuntu partition and the swap file. When I tried to grow the XP partition  I was allowed practically no growth.  How can I get the XP partition up to a much larger soze?

---

### Post by Gazneth on 2007-06-23
I did the same thing you are trying a few weeks ago, try booting up with your live cd and using the gpartd there.  On the live cd it's available under System/Admin  called disk manager I think.:D

---

### Post by BobCFC on 2007-06-23
You have to unmount a partition to resize it.   You can also get a special [Gparted LiveCD]("http://gparted.sourceforge.net/livecd.php") which is only about 50mb download.  Just burn ISO to cd to use as a recovery disk.

---

### Post by euler_fan on 2007-06-23
GParted is also part of the Ubuntu Live CD. You can boot from the Live CD and it is under System->Administration and it it is called something I can't remember right now.

Good luck.

---

### Post by thefowlstar on 2007-06-23
Well, from what I understand, you're simply resizing the Ubuntu partition. Try moving the partition to another corner so you have room to grow the XP partition.

> **euler_fan said:**
> GParted is also part of the Ubuntu Live CD. You can boot from the Live CD and it is under System->Administration and it it is called something I can't remember right now.

Good luck.

I also don't remember if it's on the menu, but you can open up a terminal and type: > sudo gparted to run it.

---

### Post by henthorn on 2007-06-24
How does one unmount a partition in order to resize it?

---

### Post by bigken on 2007-06-24
if you use the gparted liveCD you dont need to unmout

---

### Post by jrev on 2007-06-24
You can resize your partitions but you cannot move the beginning point.
So you better think about it before you start your first partitionning

---

### Post by dptxp on 2007-06-24
You can not do what you want.
Best option is to save Windows data files in Linux partition, or still better resize the Linux partition and make a FAT32 partition in the free space.
10 GB should be good enough for all Windows program files.
To see the partition in Linux, you have to mount it.

---

### Post by logos34 on 2007-06-24
> You can not do what you want.
Best option is to save Windows data files in Linux partition, or still better resize the Linux partition and make a FAT32 partition in the free space.
10 GB should be good enough for all Windows program files.
To see the partition in Linux, you have to mount it.

I agree.  No need to start moving things around.  Just turn it (the ~67gb freed space)  into a data storage partition--a sort of combined /home and /My Documents partition.  Ext3, fat32, ntfs--it really doesn;t matter as there are drivers to enable r+w for everything (fs-driver for windows ext2/3 r+w, ntfs-3g for linux).  Fat32 is fine except it fragments more easily and hasa 4gb file size limit (so no big video files, image backups, etc).  That's the way I have my win xp set up--system files on a 7.8gb partition, everything else on data partition.  Makes reinstall a cinch and the same goes for a linux install with your saved docs and settings on /home.

add: check out the ubuntu section over at psychocats.net--there's a page (sorry don;t have the exact link handy) with nice pictures of dual boot partitioning setups.

---

### Post by henthorn on 2007-06-24
Since my XP partition is ntfs I guess the new data partition should also be ntfs, right? I have limited computer knowledge and don't understand having a separate data partition.  Do the programs themselves also go in that partition? If that is so then I can understand how a re-install would be less time consuming. It seems some programs are autmatically installed on the C drive without giving one a choice.  How is that handled?

---

### Post by logos34 on 2007-06-24
> Since my XP partition is ntfs I guess the new data partition should also be ntfs, right? I have limited computer knowledge and don't understand having a separate data partition. Do the programs themselves also go in that partition? If that is so then I can understand how a re-install would be less time consuming. It seems some programs are autmatically installed on the C drive without giving one a choice. How is that handled?

well, your windows systems files go into C:\, and I just let all the other programs I install go by default to that directory because when you reinstall windows you're going to have to reinstall the programs again.  (Of course that means you have to be careful to backup any configuration files/custom settings associated with those programs to your data partition, but no big deal).  Everything under My Documents and the like is on the data partition and never gets touched by the reinstall.  You just modify your start menu to point to point to 'My...' on the data parition.  ntfs or fat32

---

### Post by dptxp on 2007-06-25
> **logos34 said:**
> well, your windows systems files go into C:\, and I just let all the other programs I install go by default to that directory because when you reinstall windows you're going to have to reinstall the programs again.  (Of course that means you have to be careful to backup any configuration files/custom settings associated with those programs to your data partition, but no big deal).  Everything under My Documents and the like is on the data partition and never gets touched by the reinstall.  You just modify your start menu to point to point to 'My...' on the data parition.  ntfs or fat32

You can reinstall if mounting partitions seems difficult to you. 
You can delete the Ubuntu Partition and resize it to smaller size increasing
Windows Partition.

You resize Windows partition or not, what has been suggested sounds best to me.
Separate Data partition is the correct way.

10 GB - Windows
The extended partition - Primary OR Logical
6-8 GB - Linux / (root ) ext3
Left Space less 1 GB - /home (ext3) - Can use the not so liked FAT32
1 GB - SWAP

If you move all your data to the /home partition, 10 GB shall be enough for Windows.

---

