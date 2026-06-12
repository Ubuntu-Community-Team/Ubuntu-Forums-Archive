---
title: "External Hard Drive with Ubuntu/XP system"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Jeff Gavett on 2006-08-28
I'm looking into getting an external hard drive to store the large audio files I work with in recording, and while I'm looking forward to flattening Windows once I back all my important files up, I'm looking forward even more to really trying out Ubuntu.

Is there anything I should know about working with multiple OS partitions and an external hard drive? Preferably I'd like to have seperate backups for both my OS's entire partitions in addition to a repository for large files. Would this be possible with Ubuntu's file system needs?

---

### Post by Skia_42 on 2006-08-28
If the two OS's are on seperate partitions I do not see how there could be any problems. As far as your partition for large files, I am assuming you want that accesible from Windows and Ubuntu, the "msdos" and "FAT32" file system types are both supported in Linux, you should be fine. just be sure you have enough room on your drive. ;)

---

### Post by Metacarpal on 2006-08-28
I've not worked with multiple partitions on an external drive, but I recently salvaged the hard drive out of a friend's Mac Powerbook, using a USB mounting case, and it detected automatically.  It did list it specifically as being a hard drive, so you shouldn't have any problems partitioning, etc.  I believe it mounted as sda1.

---

### Post by Shadyman on 2006-08-28
For an external drive, I use an EXT3 partition. You can get EXT2 drivers for Windows XP [Here]("http://www.fs-driver.org/").  (EXT3 is backwards compatible with EXT2). The advantage is, you get the journaling file system when mounted on Linux, and you also have Windows access.

One thing I found, though, is you have to "eject" or "remove safely" before unplugging it from Linux.

I prefer EXT3 to msdos or fat32 for one reason. Well, Ok 2. First one being 4K block size instead of 32k block size in fat32, not that it would matter much for big media files.  Secondly, I like the journaling option of the file system when you're on Linux; If something happens like the power goes out or you unplug the drive or something like that, you can recover better (and faster) than with fat32 because it keeps a record of what it does.

Example:
I save a file.
The disk records that it's writing blah blah blah to block xyz.
It writes blah blah blah to block xyz
It erases the journal record.

If something happened to the drive during any time in that process, it can restart, say "Hey, it still has something in the journal." Now instead of having to scan the whole drive for what happened ('bad sectors' and such), it knows exactly what blocks are affected, and can go to work fixing them.

Keeping in mind this is a very simplistic example, and correct me if I'm wrong, it's been a while since I studied up on how that stuff works exactly, but that's my understanding of it.

You may choose FAT32, and it may be the better choice for you, I just thought I'd give you another option :KS

---

