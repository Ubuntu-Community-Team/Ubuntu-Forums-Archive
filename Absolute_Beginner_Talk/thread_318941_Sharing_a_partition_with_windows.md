---
title: "Sharing a partition with windows"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by gardara on 2006-12-14
I'm wondering if it's possible to share a partition with ubuntu and windows i.e. if I am dual booting and have windows on one partition and ubuntu on the other, then I would have the third partition where I could store my files that I want to access from both windows and ubuntu.
Is this possible? and is this adviced?

I'm thinking about this as I would like to use some windows software to encode videos but I w uld like to play them in ubuntu as ubuntu is my primary OS.
Would it maby be better to have a windows partition and a ubuntu partition and a small shared partition, just so I would be able to move the files I want from windows to ubuntu.


Hope you get what I'm trying to say.

:)

---

### Post by Shatrat on 2006-12-14
You could make a data partition formatted as Ext3 and use fs-driver to read and write in windows.  You could also make it ntfs and still be about to mount it in linux, but the write support is a little touchy then I gather.
[http://www.fs-driver.org/](http://www.fs-driver.org/)
I use fs-driver on my dual boot system and it is really transparent on the windows side, you can't tell that youre not dealing with an NTFS partition.  On the linux side it's kind of annoying seeing little thumbs.db files pop up in some of the directories and stuff but that will happen with any system windows is allowed to write on.

---

### Post by yabbadabbadont on 2006-12-14
> **Shatrat said:**
> You could make a data partition formatted as Ext3 and use fs-driver to read and write in windows.  You could also make it ntfs and still be about to mount it in linux, but the write support is a little touchy then I gather.
[http://www.fs-driver.org/](http://www.fs-driver.org/)
I use fs-driver on my dual boot system and it is really transparent on the windows side, you can't tell that youre not dealing with an NTFS partition.  On the linux side it's kind of annoying seeing little thumbs.db files pop up in some of the directories and stuff but that will happen with any system windows is allowed to write on.

Or just make a regular fat32 partition and mount it as vfat.  Then there isn't any need for extra drivers in either OS.

---

### Post by moshuptrail on 2006-12-14
Here's a link to a pretty  good discussion about just what you are thinking:

[partitioning with windows]("http://ubuntuforums.org/showthread.php?t=318235")

---

### Post by dmizer on 2006-12-14
both linux and windows can nativly read and write to fat32 file system.  but the problem with fat32 is that large file support is lacking.  so if you're planning to frequently share files larger than 4gb, then you'll have to look into configuring linux to support ntfs, or configuring windows to use ext3.

---

### Post by gardara on 2006-12-14
Wow, I forgot how fast this forum is.
I posted this topic to have hopefully gotten some replies tomorrow morning.

Thanks for your replies, I'll read better trough them tomorrow at work :)

---

