---
title: "Partitioning Question"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by TriJump on 2006-08-19
Hi All,

   Im fairly new to Linux and am in the process of installing Ubuntu onto my laptop that has xp Pro running on it now.  I've backed up my files, and defragged many times.  I'm now to the point in the install where it asks about partitions.  I know that I could just click and let the installer do it all for me, but I'd prefer to learn how to do it on my own.  So currently I have a 100 gig hard drive, 93 of it available.  I primarily use this as a windows machine and I've already got a lot of music on it - so I've decided to give my Windows partition 60 gigs.  Then I was thinking about 5 gig for a / partition, 15 gigs for a /home partition, 1 gig of swap, and 12 gig on a FAT32 file system so I can transfer files between XP and Ubuntu.  The problem that I'm running into is the limit on primary partitions.  All told I've got 5 partitions so I know I need to make one of them extended and include two logical partitions in that one.  My question is does it matter which two partitions I place in the extended partition?  Originally I had the swap and FAT32 partition in the extended partition, but I didnt know if I should put the /home instead of the FAT32?  Any help you guys can provide would be greatly appreciated.

---

### Post by secretlondon on 2006-08-19
I'm not sure about most of your points - but I'd recommend a FAT32 partition. There is a way of getting read/write access to ntfs partitions but it's not supposed to be entirely safe. 

I'm not an expert but I allowed Ubuntu to organise my free space the way it wanted. I have an ntfs partition, a fat32 one for shared docs, the main ubuntu one, and a swap one. root and /home and everything else are in the same partition.

---

### Post by djsroknrol on 2006-08-19
That depends on how the drive is set up really....Is that partition all alocated as one now?...in other words, is the 93GB all one piece?

If it is then you need to "shrink" it down with something like GParted live CD to make room for the Ubuntu install..After you have room then go with your install..it sounds just fine.

Go ext3 not fat32...ubuntu can talk to windows folders just fine with a little work. Ext3 is far better than fat32.

---

### Post by seshomaru samma on 2006-08-19
You can make your Windows a primary partition , then have an extended partition for your files (FAT32)
Next make / primary 
and /home primary
I don't know what'd the limit but if you can't make swap primary you can have it as extended , no problem.
Why is your Windows partition so big? The whole OS can't be more than 8GB at most. Maybe you have a lot of programmes installed ?
You can put all your files in the FAT32 partition (including music) and easily share it with Ubuntu.

edit: it's correct , ext3 is better than Fat32, to access it from Windows , you will need [THIS ]("http://www.fs-driver.org/")

---

### Post by TriJump on 2006-08-19
Yeah it is all one partition currently, but I'm using GParted and I shrank it down to 60 for the windows one.  And I had always heard that in order for Windows and Linux to share files there needed to be a FAT32 partition because windows cant read and write to ext3 and linux cant read and write to ntfs?  If it is possible to read ext to ntfs and vice versa - could you elaborate a little?  Thanks.

---

### Post by kopo88 on 2006-08-19
Don't bother with a FAT32 partition. Make your "/home" ext3 partition 27 GB (15+12) instead. There's a program for Windows called EXT2 FS ([http://www.fs-driver.org/](http://www.fs-driver.org/)) that makes ext2/ext3 partitions fully accessible in Windows (read and write). You'll be able to share files between the the OSs in your Linux /home directory, without any problems.
And I think that should bring you within the limit for the number of primary partitions.

---

### Post by secretlondon on 2006-08-19
> **djsroknrol said:**
> That depends on how the drive is set up really....Is that partition all alocated as one now?...in other words, is the 93GB all one piece?

If it is then you need to "shrink" it down with something like GParted live CD to make room for the Ubuntu install..After you have room then go with your install..it sounds just fine.

Go ext3 not fat32...ubuntu can talk to windows folders just fine with a little work. Ext3 is far better than fat32.

But windows can't write or read to ext3..

If you want a shared windows/linux data partition you have 2 choices - ntfs or fat32. Linux doesn't write to ntfs very happily, so I'd use FAT32 for shared data that both windows and linux have to be able to read and write.

---

### Post by secretlondon on 2006-08-19
> **kopo88 said:**
> Don't bother with a FAT32 partition. Make your "/home" ext3 partition 27 GB (15+12) instead. There's a program for Windows called EXT2 FS ([http://www.fs-driver.org/](http://www.fs-driver.org/)) that makes ext2/ext3 partitions fully accessible in Windows (read and write). You'll be able to share files between the the OSs in your Linux /home directory, without any problems.
And I think that should bring you within the limit for the number of primary partitions.


Ooh - I didn't know that!

---

### Post by seshomaru samma on 2006-08-19
> **TriJump said:**
> Yeah it is all one partition currently, but I'm using GParted and I shrank it down to 60 for the windows one.  And I had always heard that in order for Windows and Linux to share files there needed to be a FAT32 partition because windows cant read and write to ext3 and linux cant read and write to ntfs?  If it is possible to read ext to ntfs and vice versa - could you elaborate a little?  Thanks.

It's possibe for Windows to read ext2/3 , please see the link in the 'edit' part of my previous post.
It's also possible for Linux to read Fat32. 
Both options are cool.
Getting a FAT32 is easier if you are not that familiar with Linux, but Ext3 is better in the long run.

---

### Post by TriJump on 2006-08-19
Awesome guys - thanks for the help.  And thanks for the link Kopo - it is all greatly appreciated.

---

### Post by secretlondon on 2006-08-19
> **seshomaru samma said:**
> It's possibe for Windows to read ext2/3 , please see the link in the 'edit' part of my previous post.
It's also possible for Linux to read Fat32. 
Both options are cool.
Getting a FAT32 is easier if you are not that familiar with Linux, but Ext3 is better in the long run.

Out of the box linux can read ntfs (but not write), and read and write to FAT32.

The link posted by kopo provides a program that allows windows to read and write to ext3.

---

### Post by TriJump on 2006-08-19
So will fs-driver allow me to read and write from windows to ext3?  And will I also be able to read and write to ntfs from linux?  It sounds to me that in order to read and write from both OS's it would be a bit easier to make a fat32?

---

### Post by seshomaru samma on 2006-08-19
> **TriJump said:**
> So will fs-driver allow me to read and write from windows to ext3?  And will I also be able to read and write to ntfs from linux?  It sounds to me that in order to read and write from both OS's it would be a bit easier to make a fat32?
the fs-driver allows Windows to write to ext2 or ext3 (but has no LVM support)
linux usually has difficulties writing to ntfs but can easily write to fat32
i think both fat32 and ext3 are good solutions

---

