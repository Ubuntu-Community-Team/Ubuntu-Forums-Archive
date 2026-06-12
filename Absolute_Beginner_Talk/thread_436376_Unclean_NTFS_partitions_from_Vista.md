---
title: "Unclean NTFS partitions from Vista"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by dbvanhorn on 2007-05-07
I scrubbed vista off my machine, and installed 7.04

Everything's going well, except that I can't see several partitions.

/dev/hdc, /dev/sdb, /dev/sdc all report that they are "unclean".
The repair instructions I've seen all contain the phrase "unless you are running vista", but I haven't seen what to do about it if you were running vista.

The partitions in question contain about a terabyte of data I'd hate to loose.
They were fine under Vista, scandisk didn't report any problems.

typical output:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

---

### Post by jargoman on 2007-05-07
I've never used vista I'm a linux user. 

I do know that you can insert a windows xp installation disk  press r for repair mode then in the ntfs partition run 

$ chkdsk /r

this will "clean" the ntfs file. An unclean filesystem is s result of not shutting down properly before cutting the power

---

### Post by zander3213 on 2007-11-19
I have tried an xp installation disk and a vista one, my computer just goes to a black screen.  Is there any other way to clean an NTFS partition?

---

