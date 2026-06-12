---
title: "What Partition Format Should I Be Using For This?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by NoVista on 2007-06-11
Currently unning Feisty on ext3.

So when it comes to the saving of all my audio/video files, and all my other stuff, is ext3 the partition format I should be using?

Throw away any Linux/Windowz/Whoever wars, I'm simply asking what partiton type is the best. I always thought of NTFS as probably the best format. Am I wrong? Since Ubuntu is my OS, should all partitions on all hard disks now be ext3?

---

### Post by bobplano on 2007-06-11
since you are using ubuntu as your main OS ext3 would be best. i don't know the "true" best format, but you do have to defrag fat32 and NTFS, but not ext3.

---

### Post by Inxsible on 2007-06-11
EXT3 offers journalling. It is not the only one that offers it, but I am sure FAT32 and NTFS dont. FAT32 limits the size of a file to less than 4GB among other issues. You will probably not see the effects of journalling immediately, but it does help in the long run.

---

### Post by Inxsible on 2007-06-11
Quote from Wikipedia

> File systems tend to be very large data structures; updating them to reflect changes to files and directories usually requires many separate write operations. This introduces a race condition, in which an interruption (like a power failure or system crash) can leave data structures in an invalid intermediate state.

For example, deleting a file on a Unix file system involves two steps:

   1. Removing its directory entry.
   2. Marking space for the file and its inode as free in the free space map.

If step 1 occurs just before a crash, there will be an orphaned inode and hence a storage leak. On the other hand, if only step 2 is performed first before the crash, the not-yet-deleted file will be marked free and possibly be overwritten by something else.

Recovery in a non-journaled file system requires a complete scan of the data structures and correction of inconsistencies. This method can be inefficient in case of a high-capacity file-system with low input/output bandwidth.

A journaled file system maintains a journal of the changes it intends to make. In case of disruption, recovery involves reading the journal and replaying to restore consistency. The changes are said to be atomic (or indivisible); they either

    * succeed (have succeeded originally or be replayed completely during recovery), or
    * are not replayed at all.

Some file systems allow the journal to grow, shrink and be re-allocated just as would a regular file; most, however, put the journal in a contiguous area or a special hidden file that is guaranteed not to move or change size while the file system is mounted.

A physical journal logs verbatim copies of blocks that will be written later, such as ext3. A logical journal logs information about the changes in a special, compact format, such as XFS. This reduces the amount of data that needs to be read from and written to the journal in large, metadata-heavy operations (for example, deleting a large directory tree).

In Log-structured file systems, the journal is the file system. Common Unix file systems are usually not log-structured, but the WAFL and Reiser4 borrow some techniques from log-structured file systems.

---

### Post by Bachstelze on 2007-06-11
XFS is known to be the best-performing one when it comes to handling lots of large files. ext3 will still perform reasonably well. Avoid ReiserFS since it's mosly designed for small partitions/files. NTFS and FAT are both out of the question.

---

### Post by NoVista on 2007-06-12
Wow, lots of great info everyone.

I'm not familiar with XFS, and I do have large files.

Interesting .. ..

---

### Post by revertex on 2007-06-14
> **HymnToLife said:**
> Avoid ReiserFS since it's mosly designed for small partitions/files.

ReiserFS mosly designed for small partitions? seriously?

---

### Post by eldepeche on 2007-06-14
> **revertex said:**
> ReiserFS mosly designed for small partitions? seriously?

Well, one of its main features is writing multiple files in a single block. With most setups, the block size is 4K, so if there are a lot of small files, say around 1K, then you're wasting a lot of space.

---

### Post by Bachstelze on 2007-06-14
> **revertex said:**
> ReiserFS mosly designed for small partitions? seriously?

Ok, we'll do something. you make a 200 GiB ReiserFS partition, you try to mount it, and you call me when it's done :D

*goes away to make some tea*

---

### Post by revertex on 2007-06-14
i don't know what you mean, i've got 240Gb in my box, splitted with several reiserfs partitions, where the biggest one have 160Gb, and a server with 570Gb, where the biggest one have 240Gb and didn't noticed any slowndown to mount partitions.

---

### Post by Atomic Dog on 2007-06-14
Geek fight!  Pass the popcorn!

Seriously, Ext3 should be fine.  Jut my opinion.

---

### Post by dptxp on 2007-06-14
I found this at Wiki.
No mention of Partition Size.
I prefer EXT3, had shortlisted after a good study on Net.
Windows can be made to read ext3.


Compared to ext2 and ext3 in version 2.4 of the Linux kernel, when dealing with files under 4 KiB and with tail packing enabled, ReiserFS is often faster by a factor of 10–15.[citation needed] This is of great benefit in Usenet news spools, HTTP caches, mail delivery systems and other applications where performance with small files is critical.

Criticism

Some directory operations (including unlink(2)) are not synchronous on ReiserFS, which can result in data corruption with applications relying heavily on file-based locks (such as mail transfer agents qmail[3] and Postfix[4]) if the machine halts before it has synchronized the disk.[5]

There are no programs to specifically defragment a ReiserFS file system, although tools have been written to automatically copy the contents of fragmented files hoping that more contiguous blocks of free space can be found. However, Reiser4 will have a repacker that optimizes file fragmentation.[6]

fsck

The tree rebuild process of ReiserFS's fsck has attracted much criticism: If the file system becomes so badly corrupt that its internal tree is unusable, performing a tree rebuild operation may further corrupt existing files or introduce new entries with unexpected contents

---

### Post by hyper_ch on 2007-06-15
> **HymnToLife said:**
> Ok, we'll do something. you make a 200 GiB ReiserFS partition, you try to mount it, and you call me when it's done :D



Phone #?

---

