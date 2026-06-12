---
title: "Fat32"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by cypherzero on 2007-05-05
I formatted my hard disk as FAT32 so Linux and Windows could access its files (from what I've gathered Linux and NTFS have 'issues').

I thought Linux was fine with FAT32 until I came to 'bunzip2' a rather large file (bzipped with cygwin) - which Linux simply refused displaying an IO error - I had to use Windows to get actually the data out.

Is this a freak incident or is FAT32ing a 400Gb disk not a good idea?

---

### Post by taurus on 2007-05-05
Is the file bigger than 4GB?  Otherwise, there shouldn't be a problem writing to it either from Ubuntu or Windows.

---

### Post by cypherzero on 2007-05-05
The file is around 250Mb, I'd have thought it was possibly due to using cygwin to compress it apart from the 'possibly could not write to disk' error.
I'm more concerned with if I should be using FAT32 or something else.

---

### Post by Tsen on 2007-05-05
Well, NTFS really isn't too big a deal anymore.  NTFS-3g, which lets you read NTFS from Linux, has reached 1.0--a stable release--so it works pretty much flawlessly.  I've never had trouble with it before.
Also, look at the ext2 driver for Windows.  It's simple, small, and also works flawlessly with ext2 and ext3 filesystems, so you can access them from Windows.  
These both support files larger than 4GB (Like DVD .iso's, which caused a lot of trouble for me), so they should work much better.  Also, ext3 doesn't fragment, which is a plus, and NTFS is supposed to be marginally better at stopping fragmentation than FAT32.

---

