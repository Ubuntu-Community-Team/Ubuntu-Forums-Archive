---
title: "Can a Mac running OS X read an ext3 drive, NTFS?"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by SlappyPappy on 2008-04-11
Wondering what would be the best file format for an external hard drive. I have someone who is going to have to take files off of my drive and they're using OS X.

Should I use NTFS or ext3? Something else? 

Thanks for the help.

---

### Post by stchman on 2008-04-11
> **SlappyPappy said:**
> Wondering what would be the best file format for an external hard drive. I have someone who is going to have to take files off of my drive and they're using OS X.

Should I use NTFS or ext3? Something else? 

Thanks for the help.

Mac OS X is based off the FreeBSD kernel.  The FreeBSD kernel does support NTFS and EXT3.  Apple may have removed that capability from the kernel so you will have to read on it.

---

### Post by aeiah on 2008-04-11
link: [yes, but only with this, perhaps](http://sourceforge.net/projects/ext2fsx/)

---

### Post by Jonne on 2008-04-11
there's FUSE for mac (google it), which should allow you to mount NTFS at least but probably any other arbitrary filesystem too.

---

### Post by aeiah on 2008-04-11
the easiest thing of course is to format it as FAT, but that starts to get annoying when you deal with files above 4GB, since it cant handle them. it'll work out of the box with linux, windows and mac systems though.

---

