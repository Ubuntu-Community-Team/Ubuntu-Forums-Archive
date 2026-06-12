---
title: "What formatting to use for shared Linux/XP drive?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by toecutter on 2007-03-19
From what I understand by reading the Ubuntu Bible and a few sites:

[LIST]
[*]Linux can't write to NTFS but can read from it
[*]Linux can read/write to FAT32 file systems
[*]XP can't read the Linux formatting (ext2 and ext3) but programs exist to allow XP to do this
[/LIST]

So...if I want to share, say, a movies/MP3/whatever drive between XP and Ubuntu systems, I'm guessing the best thing to use is FAT32?

---

### Post by buuntuu! on 2007-03-19
if you don't want to install drivers, yes.
but fat32 isn't the newest of filesystems. max filesize is 4gb, so if you've got something bigger than this...
there is [http://www.fs-driver.org/]("http://www.fs-driver.org/") letting window$ read/write to ext3,
and [http://www.ntfs-3g.org/]("http://www.ntfs-3g.org/")letting linux write to ntfs. read-access is default! so if you just want to migrate from window$ to linux, no need to do anything

---

### Post by justleen on 2007-03-19
> **buuntuu! said:**
> if you don't want to install drivers, yes.
but fat32 isn't the newest of filesystems. max filesize is 4gb, so if you've got something bigger than this...
there is [http://www.fs-driver.org/]("http://www.fs-driver.org/") letting window$ read/write to ext3,
and [http://www.ntfs-3g.org/]("http://www.ntfs-3g.org/")letting linux write to ntfs. read-access is default! so if you just want to migrate from window$ to linux, no need to do anything



I'd go with fat32.. There is the 4gb limit, but in my expierince thats quite workable (unless your pumping large vid files over)

---

### Post by buuntuu! on 2007-03-19
... there is always the maintenance-issue, fat32 tends to fragmentation, so you'd have to tidy up from time to time...

---

### Post by ahmatti on 2007-03-19
I use ext3 with an extra *free* driver for windows: [http://www.fs-driver.org/](http://www.fs-driver.org/). It works perfectly for me and this way I also get to access my home directory from windows and even the root file system if needed. I haven't got any stability problems in windows.

4 hg limit can also be a problem if you wan't to run e.g a virtual machine and obviously when working with DVD's as mentioned.

---

### Post by steve101101 on 2007-03-19
I use UFS for my server that shares to windows and linux computers.

---

### Post by AlanD on 2007-03-19
I find a small partition in FAT32 for transferring files between OS' has worked best for me. Keeps either OS from messing around with the system of the other OS by accident.

---

### Post by toecutter on 2007-03-19
Ahhhh... forgot about the max drive size of FAT32 (it's been a loooong time since I switched to NTFS!)

I'll give the fs-driver.org proggie a try - since it looks like I'll be using Ubuntu more than XP I'd rather not have a workaround for my main OS :)

Mucho thanks for the tips, guys! :)

What is the better (for speed and defragging needs) file system to use - EXT2 or EXT3?

Finally, if I want to set up an Ubuntu-based media server that will be accessed by various machines, what would be the best (as in friendliest for Windows and Linus) file system to use?

---

