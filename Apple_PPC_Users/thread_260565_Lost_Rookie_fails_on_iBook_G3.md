---
title: "Lost Rookie fails on iBook G3"
date: 2006-09-18
forum: Apple PPC Users
---

### Post by meyerfun on 2006-09-18
Okay.  I'm trying to create a dual boot Mac iBook.  I booted from an external drive and partitioned the drive into 8GB (first partition) and 22 GB (second).  I did NOT, however, change it from hfs and journaled.  I cloned my old OS and home onto the 22 GB partition, and attempted install "dapper" from the download live CD.

The install menus were terrible, because I couldn't figure out how to change the screen resolution (imagine clunky moves using option drage to view the whole screen).

Although I read that choosing "free space" with the free space being in the first partition would take care of things, it didn't.  I went back and tried to turn off journaling on the ubuntu partition, but everything clunked.

Advice?

Any fix for the screen issue?

Reformat and partition the drive unjournaled, restore my OS X clone and install again?

Practice massive unintelligible geek entries into the terminal?

Tanks in ADwance.

Cheers,

Mfun

---

### Post by linear on 2006-09-19
Not sure about the screen issue, but you definitely need to wipe out that first partition - it sounds like you had it formatted as HFS. It really needs to be "Free Space" - not formatted at all.

---

### Post by meyerfun on 2006-09-19
Thanks for the reply.  Using Mac DiskUtility, I see four choices: All are Extended formats, with one exception, Unix file system.

Should I erase that partition as a Unix partition?

jm

---

### Post by linear on 2006-09-19
No, I don't have Disk Utility in front of me at the moment, but I believe you can set the partition size and not format at all.

---

### Post by meyerfun on 2006-09-19
That was the key.  I reformatted with an 8 GB free partition (not hfs or unix) followed by a 22 GB HFS partition (a little more than the size of my previous Mac install).  I cloned my old OS with Netrestore from a previously saved image to the hfs partition, and then struggled through the large install screens to choose "largest free space" in the partition menu, and everything seems to be moving along just fine.

Many thanks for the clues.

jm

---

