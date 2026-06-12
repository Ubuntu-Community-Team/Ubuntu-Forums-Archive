---
title: "System cleaning program for Linux?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Jake808 on 2007-04-27
I was wondering if there was an equivalent to a program like C**p Cleaner on Linux.  Something that cleans up unwanted files.  I assume that any operating system no matter how good it does things must accumulate some crud as it runs.  

Jake

---

### Post by Kobalt on 2007-04-27
There is no such program needed for Linux, Aptitude can do pretty much anything you need in that area.
See these good advices on cleaning up your system if you're interested in : [http://ubuntuforums.org/showthread.php?t=140920&highlight=cleaning](http://ubuntuforums.org/showthread.php?t=140920&highlight=cleaning)

---

### Post by Seisen on 2007-04-27
This might help

[http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")

---

### Post by Campingman on 2007-04-27
There is some instruction on removing junk files here:
[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

---

### Post by compiledkernel on 2007-04-27
fsck is the really only thing one would consider to be a filesystem clean up, much like defragmentation occurs. 

[quote=wikipedia]Generally, fsck is run automatically at boot time when the system detects that a file system is in an inconsistent state, indicating a non-graceful shutdown, such as a crash or power loss. Typically, fsck utilities provide options for interactively repairing damaged file systems (the user must decide how to fix specific problems), allowing fsck to decide how to fix specific problems (so the user doesn't have to answer any questions), or reviewing the problems that need to be resolved on a file system without actually fixing them.[/quote]

By theory ext2, ext3 styled paritions do not become fragmented to the same level that one would see with a windows FAT/NTFS parition.

---

