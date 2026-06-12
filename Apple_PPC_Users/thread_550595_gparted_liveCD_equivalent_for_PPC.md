---
title: "gparted liveCD equivalent for PPC"
date: 2007-09-14
forum: Apple PPC Users
---

### Post by wickstopher on 2007-09-14
Is there any equivalent liveCD to gparted for PPC processors?  It seems as though there must be something, but all of my searches haven't turned anything up.  I honestly don't even care if it can touch my OSX partition.  I just want to be able to create free space in my linux partition, and I can't find any free tools to do so.  gparted in the (k)ubuntu installation cds seems to be somewhat ineffectual.  I don't see any reason why it can't just write over the partition with free space, but it can't.  Thanks for any assistance!

---

### Post by pxwpxw on 2007-09-14
**wickstopher**
gparted may be having trouble with hfs+ journalling in the macosx partition. Check in macosx to see if the macosx partition is journalled. You can turn it off with diskutil in a macosx terminal.

---

### Post by wickstopher on 2007-09-14
It is indeed journaled.  Now, I'm not perfectly clear on what this means.  I know that ext3 is the "journaling" equivalent of ext2.  I'm not looking for a full-blown explanation, but will turning off journaling affect performance in osx in a big (or little) way?

---

### Post by stmiller on 2007-09-14
Journaling is a safety thing for your data. It keeps a 'journal' of every read/write so if there is a failure, or if your machine shuts off, the next time it reboots it will use the journal to repair any bad data.

NTFS is a journaling filesystem, as well as ext3.

---

### Post by Jammy4041 on 2008-04-15
This page may be of some use to you:

[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)

It is a guide to resizing HFS+ partitions using gParted. If you cannot get a gParted PPC cd, just give your Live CD a shot. Maybe it would work. Check that the MD5 somes match up, so you may have to re burn your CD/DVD. (And if you do, burn it at around 8x) Then when you boot, you may want to check the disc for errors too. 

I find that gParted usually works well, from an Ubuntu Live CD.

Anyway, the page above says to enable, then disable journalling.

---

### Post by slacka-vt on 2008-04-16
I had no problems "resizing" my ext3 partiton using the "partitioner" on the Ubuntu live cd.
system > administration > partitioner

~s

---

