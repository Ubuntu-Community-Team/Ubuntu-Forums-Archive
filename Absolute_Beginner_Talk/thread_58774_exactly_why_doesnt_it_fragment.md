---
title: "exactly why doesnt it fragment?"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by weasel fierce on 2005-08-21
What, exactly, is the reason that GNU/Linux systems dont seem to fragment ? Do they just place the files smarter or ?

---

### Post by bjweeks on 2005-08-21
Why should it fragment? We just come to think that the way it is because Microsoft used an  inferior file system.

---

### Post by nic2 on 2005-08-21
[QUOTE=weasel fierce]What, exactly, is the reason that GNU/Linux systems dont seem to fragment ? Do they just place the files smarter or ?[/QUOTE]
The reason that extX/reiser file systems run smoother without fragmenting is not in the filesystems, it is in the way the operating systems save files. If you enlarge a file in Windows and resave it, Windows will put the additional information someplace in the file system, but not necessarily with the original file. This is what causes fragmentation.

UNIX and GNU/Linux systems keep the file and its additions together in one place when they resave the file. This eliminates (mostly) fragmentation, because the file is contiguous on the disk.

---

### Post by macgyver2 on 2005-08-21
[http://www.linuxquestions.org/questions/history/350935](http://www.linuxquestions.org/questions/history/350935)

---

### Post by nad on 2005-08-21
There are several filesystems available to a GNU/Linux operating system. They all have there own implementations.

One of the algorithms used expects a file to increase in size over time, Therefore, room is left at the end. Subsequent files are written to the first group of available contiguous blocks that is the correct size and so on. As your filesystem fills up, some files will necessarily become fragmented.

This is extremely simplified. As usual, the easiest way to defragment any filesystem is to copy it to a fresh partition.

---

### Post by cwaldbieser on 2005-08-21
[QUOTE=weasel fierce]What, exactly, is the reason that GNU/Linux systems dont seem to fragment ? Do they just place the files smarter or ?[/QUOTE]

Here is a quote from  [http://www.answers.com/topic/defragmentation](http://www.answers.com/topic/defragmentation)  that seems to explain it in layman's terms:

> Defragmentation issues

The presence of immovable system files (or of files that the defragmenter will not move in order to simplify its task), especially a swap file, can impede defragmentation. ntfsresize can safely move these files in order to resize an NTFS partition.

Certain file systems exhibit a greater susceptibility to fragmentation than others, for example, a FAT file system becomes fragmented much more quickly than NTFS. Many file systems on Unix-like platforms, such as ext3 and xfs do not provide the ability to explicitly defragment at all. These systems attempt to keep fragmentation below a certain point so defragmenting is not necessary. This fragmentation resistance works well as long as the file system has a fairly large amount of space free.

On systems without fragmentation resistance, fragmentation builds upon itself when left unhandled, so daily defragmentation is necessary to keep disk performance at peak and avoid the excess overhead of less frequent defragmentation. 

So it would seem that ext3 just makes a very good up-front effort to keep fragmentation to a minimum while a system like FAT lets the problem compound upon itself until it turns into a real problem.

That said, I also noticed some articles that said some there had been talk of adding some kernel level hooks to allow user-level tools to actually run a defragger for an ext3 filesystem.

I also read (and I may be interpreting this wrong), that the ext3 filesystem can defragment itself when it gets mounted, and it automatically does this after bien mounted so many times.  I have observed that every so often when rebooting, my system will do a manadatory fsck, so maybe that (among other things) is what's going on.

---

