---
title: "How do i access ubuntu files from xp?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by hrolfp on 2007-06-17
Hi,

I've installed ubuntu and I love it, but I occasionally use my xp partition for working in applications such as solidworks and ANSYS. I'd like to listen to the music that I've stored in ubuntu while I do this though, so is there a way for me to access my ubuntu files while working in xp?

---

### Post by steve.horsley on 2007-06-17
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by sdlcman on 2007-06-17
I'm learning all this by trial and error.

By default, XP will format a partition in NTFS.  You can opt to format in FAT 32.

Linux will read and write to FAT 32.   Linux can read an NTFS partition but will not write to NTFS.

Therefore, if you keep a FAT32 partition you can use it freely with both XP and Linux.

XP will not read an ext2 or ext3 Linux partition.

A Linux partition utility such as Gnome Partition Editor is helpful, but be advised that these are high powered utilities that can wipe out your partitions in the blink of an eye.

---

### Post by eoghanmurray on 2007-06-17
Ubuntu will read/write to an NTFS partition. Just install ntfs-3g.
See the link below for more:

[Click here to advance to <ntfs-3g> setup instructions.]("http://ubuntuforums.org/showthread.php?t=217009")

Good luck!

---

### Post by steve-shinn on 2007-06-17
Ubuntu Feisty (and possibly others) definately CAN write to NTFS partitions !! I know because I have been doing it today ....... copying some music with ogg extensions to an external HDD which was formatted in NTFS.

---

### Post by Regel on 2007-06-17
And windows can read ext3 partitions and write to them if you install ext2/3-driver.

---

### Post by coffeecat on 2007-06-17
> **sdlcman said:**
> XP will not read an ext2 or ext3 Linux partition.

Not in a default install, true, but if you had followed the link in the previous post to yours, you would have found that it can be made to.

**hrolfp**, follow the link steve.horsley gave you. I've used fs-driver as well and it seems to work just fine.

---

### Post by sdlcman on 2007-06-19
He really should just format a partition in FAT 32.

I have followed every instruction and to no surprise to me Linux will not write to an NTFS drive nor will Windows even open an Ext 3 partition.  In fact, Linux will no longer mount the NTFS drive, and I have followed every single instruction for that to no avail.  This is typical of the novice experience in Linux.  You people left out a few steps, like revising the source code in C and recompiling and then rebooting, and then typing umpteen complicated commands at the command prompt, and downloading this and that and so on.

---

### Post by jusmurph on 2007-06-19
Fat32 is a work around rather than a solution.

NTFS 3G & FS-Driver **works**... it has been for along time, perhaps you should look into it again sdlcman.

---

### Post by sdlcman on 2007-06-19
I have to admit that I've persisted and finally gotten Windows to open an Ext 3 partition.  But I was never able to get Linux to write to an NTFS partition.

I took a 40M external hard drive and partitioned it, with half being NTFS and half being ext 3.  At first Linux would read the NTFS.  I installed the additional software, and still couldn't get it to write to the NTFS partition.  Even worse, the computer locked up solid, requiring a power down power up.  After that, Linux would not mount the NTFS partition ever again, even though Windows had no problems with it.  I played around with for quite a while before reformatting the drive and starting all over again, this time in FAT 32, which I knew would work.

---

