---
title: "ext3 or reiserFS ?"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-05-29
I'm about to install ubuntu but I don't know what file system should I use
ext3 or reiserFS...
and what about the recent filr systems that I've heard about
jfs and xfs ?
wich is better of them ? (jfs,xfs)
I have read the help topics for the linux file systems but I'm still unshoure what to chose...

p.s

if I understood correctly I should convert fartition C: - were winxp installed to fat32 and the installation ubuntu partition to ext3 or reiserFS...
I want to keep winxp and I don't want to delete/resize partition b/z of my multi partitions.

thanx ahead !!!

---

### Post by az on 2006-05-29
[QUOTE=MAXDDARK]if I understood correctly I should convert fartition C: - were winxp installed to fat32 and the installation ubuntu partition to ext3 or reiserFS...
I want to keep winxp and I don't want to delete/resize partition b/z of my multi partitions.
[/QUOTE]
You cannot convert NTFS to fat, AFAIK, but I don't use windows....

Just use the default filesystem - ext3.  Use the installer to partition your drives.  No need to do any partitioning beforehand.

---

### Post by H.E. Pennypacker on 2006-05-29
> I'm about to install ubuntu but I don't know what file system should I use
ext3 or reiserFS...

They have advantages over the other, and I know ReiserFS is the more up to date one, but newest isn't always the best.  That's because everything may not support all the new stuff.  It's best go with the middle ground, so go with ext3.  It's a fine filesystem.

> and what about the recent filr systems that I've heard about
jfs and xfs ?

Maybe some day you'll find a reason to use another filesystem, but if you are  checking out Linux now, and you simply want to see what it's like, go with what is most common (ext2 and ext3, but go with ext3).  Don't worry about all the other stuff for now.

> if I understood correctly I should convert **fartition C:**

lol..good one.  Haven't thought of "fartition" before.  

>  - were winxp installed to fat32 and the installation ubuntu partition to ext3 or reiserFS...

I feel most comfortable with partitioning my hard-drive with GParted.  I don't know if Ubuntu uses GParted, but it's definitely great.  I haven't had any problems so far using GParted, and I've used it a bunch of times.  No data loss.  I like to partition the HD before I install things, because, truth be told, I don't trust patitioners that come with installation CDs, at least not the one I was thinking of using before.  I was installing PCLinuxOS, and the installer offered to partition the HD with its own paritioner, but it also warned of data loss.  That's why I immediately went with GParted, because it's based on NTFResize, which protects partitions, instead of harming them.

Anyhow, unless Ubuntu guaruntees there's no data loss with its own partitioner, go with GParted.  Download GParted, burn the Live CD, restart, and partition.  Then insert the Ubuntu Live CD when you're done, and install Ubuntu.

> I want to keep winxp and I don't want to delete/resize partition b/z of my multi partitions.

Linux is always mindful of Windows, and it won't harm it.  It works well with Windows, but many Linux users will tell you Windows has an issue with Linux.  I am just the messenger.

---

### Post by az on 2006-05-29
[QUOTE=H.E. Pennypacker]That's why I immediately went with GParted, because it's based on NTFResize, which protects partitions, instead of harming them.

Anyhow, unless Ubuntu guaruntees there's no data loss with its own partitioner, go with GParted.  Download GParted, burn the Live CD, restart, and partition.  Then insert the Ubuntu Live CD when you're done, and install Ubuntu.
[/QUOTE]
The ubuntu installer uses the same libraries.  All linux partitioners do.

---

### Post by Denis on 2006-05-29
For your Ubuntu system: I think it's best to use ReiserFS, because it performs better than ext3 and I believe it is just as reliable. I use ext3 for the root partition, but if I had to install a fresh system, I would chose ReiserFS. You have to decide for yourself though. There's too much choice I guess... :)

I've never used XFS, but I've read that it is not very reliable (for everyday use) if you compare it with ext3 or ReiserFS. You may want to wait a bit longer before you use XFS. I'm not at all an expert though, so please correct me if I'm wrong. 

The partitioning can be done with the Ubuntu installer. You have to ability to make new partitions, to shrink existing ones and so on. It should be easy to change your partitioning scheme with this tool (if you know what you want to do of course). 

However, if you want to change some things before installing Ubuntu. I can advise the [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php"). It's a bootable CD, allowing you to adjust your partitions with a graphical tool (Gparted). 

I don't think you can convert NTFS to FAT32. But do you really need write access to your Windows partition? You could make a new FAT32 partition to use with both Windows and Linux (to share files).

---

### Post by az on 2006-05-29
[QUOTE=Denis]For your Ubuntu system: I think it's best to use ReiserFS, because it performs better than ext3 and I believe it is just as reliable. [/QUOTE]

Unless you are putting a heavy load on a filesystem with litterally millions of little files, you will not see a difference.  Reiser is best for millions (litterally) of small files, but not so performant for big files.  On a desktop system, you simply won't see any difference.

Not worth the hassle.

---

