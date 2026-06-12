---
title: "Install Ubuntu"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-03-28
SOLVED

ok, here's the deal.  my windows is fried and i LOVE ubuntu.  i'm trying to install it, but gparted won't partition the drive so i have enough free space for ubuntu.  when i try to install, the option for partitioning closest to what i want is 'use the largest continuous free space'.  will this work if i have no free space on my drive?  like, will it overwrite part of the ntfs windows partition to make room?

---

### Post by dstew on 2007-03-28
gparted is pretty careful about overwriting anything. For example, if you want to shrink a partition, but have not defragmented the file system that is in it, it will not do it. To make space for a new filesystem, you either have to reformat an existing partition, or shrink existing partitions to make room for a new one.

---

### Post by locke.dragon on 2007-03-28
can i defragment the file system from ubuntu?  that's what i need to do.

---

### Post by dstew on 2007-03-28
You can use the gparted program when you boot from the live CD. You can also make a gparted live CD and boot that [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by locke.dragon on 2007-03-28
i'm using the ubuntu live cd right now and it won't let gparted do it's job.  anything else i can do short of burning onto yet ANOTHER cd-r?

---

### Post by dstew on 2007-03-28
Can you post a screen shot of your gparted screen?

---

### Post by locke.dragon on 2007-03-28
here you go 
[http://i159.photobucket.com/albums/t147/clipsandeggs/Screenshot.png?t=1175094587](http://i159.photobucket.com/albums/t147/clipsandeggs/Screenshot.png?t=1175094587)

---

### Post by mlapaglia on 2007-03-28
if you said your windows was fried, you could also get a program like partition manager, burn it to a boot cd, and run that, it will allow you to format your hard drive.

---

### Post by dstew on 2007-03-28
It looks like you should be able to shrink your ntfs partition (/dev/sda2) to make room for a linux install. What problem are you having when you try to do that?

---

### Post by locke.dragon on 2007-03-28
[http://i159.photobucket.com/albums/t147/clipsandeggs/Screenshot-1.png?t=1175095146](http://i159.photobucket.com/albums/t147/clipsandeggs/Screenshot-1.png?t=1175095146)

---

### Post by dstew on 2007-03-28
What are the error details?

EDIT: Maybe the file system has some bad blocks. Go over to windows and do a chkdsk /f.

---

### Post by locke.dragon on 2007-03-28
GParted 0.2.5

Resize /dev/sda2 from 49.80 GiB to 33.47 GiB    ( ERROR )
     	
check filesystem on /dev/sda2 for errors and (if possible) fix them    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/sda2
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Using locale 'en_US.UTF-8'.
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 53472543232 bytes (53473 MB)
Current device size: 53472545280 bytes (53473 MB)
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 2862252 (0x2bacac): extra cluster in $Bitmap
Cluster accounting failed at 2862253 (0x2bacad): extra cluster in $Bitmap
ERROR: Filesystem check failed! Totally 2 cluster accounting mismatches.
This software has detected that your NTFS is corrupted. Please run chkdsk /f
on Windows then reboot it TWICE! Important, don't forget the /f parameter!
Afterwards you can run ntfsresize. No modification was made to NTFS.

========================================

---

### Post by dstew on 2007-03-28
Yes, follow the directions in the error message. Run chkdsk /f, reboot twice, then try to partition again.

---

### Post by locke.dragon on 2007-03-28
run it in windows...  as in...  BOOT into windows and then run the command through command prompt?

---

### Post by dstew on 2007-03-28
Yes. chkdsk is a windows utility program. gparted cannot yet repair ntfs.

---

### Post by NyteGeek on 2007-03-28
> **locke.dragon said:**
> [http://i159.photobucket.com/albums/t147/clipsandeggs/Screenshot-1.png?t=1175095146](http://i159.photobucket.com/albums/t147/clipsandeggs/Screenshot-1.png?t=1175095146)

You mentioned in your first post that you don't have enough disk space to begin with, if your whole drive is dedicated to windows and that space is full already you will need to mount the drive from a live cd  with a utility like ntfs-3g and delete some files, but I wouldn't recommend this to a new user because it's complicated and deleting the wrong stuff once you get the drive mounted could make more of a mess of your windows install. Unless there is data on the windows drive that you absolutely must have I would suggest you consider just wiping it and installing Ubuntu.

---

### Post by locke.dragon on 2007-03-28
ok.  will do.  couldn't i always just tell the installer to write over the entire drive and lose everything tho?

---

### Post by dstew on 2007-03-28
You have that option. To do it in gparted, you first delete the existing partitions, then create new ones out of the unallocated space, then format the new partitions (a swap partition doesn't need to be formatted).

---

### Post by ygarl on 2007-03-28
My PC was given as a gift (1 gHz P3!) because it was so slow, then died completely.
When I looked it over, it turned out it had Win ME (!!!!!!!) and had been fiddled about with by an over-eager teenager to unbootability.

I just reclaimed the whole drive the same way they are suggesting.

Oddly, I don't find a 1gHz Pentium 3 runs slowly at all on Linux. 

Imagine that.

---

