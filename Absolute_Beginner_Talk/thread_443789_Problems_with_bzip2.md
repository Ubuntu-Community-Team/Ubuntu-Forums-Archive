---
title: "Problems with bzip2"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Fate_David on 2007-05-14
I reformated my computer recently, but not before ziping 3 important files named fate.tar.bz2 src.tar.bz2 and area.tar.bz2 and puting them on a flash drive.  after reinstalling and getting all the other files on the flash drive set up these 3 gave me this error when trying to decompress. 

tar -xjf fate.tar.bz2

bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error exit delayed from previous errors


All the other files where not corrupted but the 3 that where bzip2ed where?  that does not sound right.  If I could get some imput on this that would be awesome!  thanks in advance.

---

### Post by mssever on 2007-05-15
> **Fate_David said:**
> I reformated my computer recently, but not before ziping 3 important files named fate.tar.bz2 src.tar.bz2 and area.tar.bz2 and puting them on a flash drive.  after reinstalling and getting all the other files on the flash drive set up these 3 gave me this error when trying to decompress. 

tar -xjf fate.tar.bz2

bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error exit delayed from previous errors


All the other files where not corrupted but the 3 that where bzip2ed where?  that does not sound right.  If I could get some imput on this that would be awesome!  thanks in advance.
Clearly, something is wrong with those files. Otherwise, you wouldn't get that message. Have you tried the suggestions in the error message? If so, what did you learn?

---

