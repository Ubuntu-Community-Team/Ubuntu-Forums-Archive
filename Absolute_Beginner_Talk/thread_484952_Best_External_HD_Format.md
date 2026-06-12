---
title: "Best External HD Format"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by sludgman on 2007-06-26
Howdy Team,

   I have been trying to get my External Hard Drive to be read on Ubuntu as of late. Been going around the forums looking for some answers and EXT2/3 caught my eye. Here's what I want to do with the drive. Currently it's used for mass storage, Music, Video, College Class Files, things that I don't want to burden a main HD with. Plus incase I ever need to format the main disc, the files are safe and sound away from the computer. What I would like to do is have that HD be able to be read and written on Ubuntu and Windows, which file system will allow such a procedure? I know Xandros was able to do it and that's one of the features I liked about it, one of the very very FEW...lol. Thanks in advance for any replies, I'll be reading a bit more incase someone answers quickly.
Edit: Current file system in use is NTFS.

Sincerely,

Matt from Chicago, Illinois

---

### Post by Metacarpal on 2007-06-26
If you want the drive to be read-write in both Ubuntu and Windows, FAT32 is your best bet.  Windows can be a bit narrow-minded in what it will or won't write.
There are EXT3 drivers for Windows, though, and I've heard they work well.  I just haven't tried them myself.

(Edit: Getting Linux to write NTFS is tricky, and can result in file system corruption.  I wouldn't advise it.)

---

