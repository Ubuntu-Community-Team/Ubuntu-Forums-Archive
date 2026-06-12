---
title: "Lost + Found?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-05-29
I've noticed that even on freshly formatted ext3 drives, a lost + found folder shows up with a big red X icon on it. Whats it for, why the X, and can I delete it?

---

### Post by freesitebuilder on 2007-05-29
I asked that here:
[http://ubuntuforums.org/showthread.php?t=388610](http://ubuntuforums.org/showthread.php?t=388610)

---

### Post by benanzo on 2007-05-29
A lost+found directory is created once for every partition.  This directory contains damaged files that were recovered during a filesystem check *(fsck)* as the result of a hard reset or other system crash.  FSCK runs routinely on most Linux systems after a designated number of times of mounting a specific partition.  If FSCK is able to recover any data, it places it in the lost+found directory of that specific partition.  Most of this data is useless.  If you find that your system is working normally, you can clean out the contents of that directory.  Otherwise, if say, you have corrupted/missing files after a crash, you might look in there to see if the data was recovered after running an fsck on that partition.

---

