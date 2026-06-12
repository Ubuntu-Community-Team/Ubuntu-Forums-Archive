---
title: "Benefits of Ext3 over NTFS"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Venerence on 2007-08-17
After turning my main computer into a dual-boot, I've been considering reformatting my NTFS secondary hard-drive (which stores all my music and videos) into Ext3, then installing a ext3 read/write program for my windows boot. As I have to modify one of the boots for compatibility anyway, I'm assuming ext3 would be the logical formatting choice.

However, I don't really know the advantages of using the ext3 formatting system, aside from it never fragmenting. Would anybody be willing to explain why ext3 is a superior format to NTFS?

---

### Post by Hobo Joe on 2007-08-17
ext3 doesn't get fragmented. But I'm to lazy to find the link that explains it. :P

---

### Post by Sbarton on 2007-08-17
Maybe if you google about the difference you may come up with some views!
regards

---

### Post by Max Luebbe on 2007-08-17
[http://en.wikipedia.org/wiki/Comparison_of_file_systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")

This does a pretty good explanation of comparing filesystems.

I'd get as much off of NTFS as possible if youre dual booting (with regards to anything thats not 100% windows centric) just because its a pain dealing with NTFS partitions in Linux.

Myself, I'm a fan of XFS and Reiser. ZFS looks promising, and I'll probably be moving to that once thats a little further along in development. (itching to get off of reiser since Hans went to jail...)

---

### Post by Venerence on 2007-08-17
> Maybe if you google about the difference you may come up with some views!
Maybe if I make a forum post about the difference I could come up with some views?

oh, and the [Google](http://www.google.com/search?hl=en&q=benefits+of+ext3+over+ntfs&btnG=Search) I did before making this post.


The wikipedia is much more helpful then the google, thanks!

---

### Post by kellemes on 2007-08-17
There are a lot of filesystems to consider, including ntfs, etx2/3, reiser etc..
It's much too complicated for me to understand, so for sharing I always use FAT32, it works great.

---

### Post by aks44 on 2007-08-17
ext3 doesn't support the so-called "alternate data streams" that NTFS has, so it can't hide data from you.

[QUOTE=Wikipedia article on NTFS]Alternate data streams allows files to be associated with more than one data stream. For example, a file such as text.txt can have an ADS with the name of text.txt:secret.txt (of form filename:ads) that can only be accessed by knowing the ADS name or by specialized directory browsing programs. Alternate streams are not detectable in the original file's size but are lost when the original file (i.e. text.txt) is deleted with a RemoveFile or RemoveFileTransacted call (or a call that uses those calls), or when the file is copied or moved to a partition that doesn't support ADS (e.g. a FAT partition, a floppy disk, or a network share). While ADS is a useful feature, it can also easily eat up hard disk space if unknown either through being forgotten or not being detected.
[...]
Care must be exercised when copying or moving files from NTFS to other filesystem types. Windows system calls and programs can have varying behavior with regard to alternate data streams and might silently strip those which could not be stored on the destination filesystem. A safe way of copying or moving files is to use the BackupRead and BackupWrite system calls, which allow to enumerate streams, to verify whether each stream could be written to the destination volume and to knowingly skip offending streams.[/QUOTE]


This alone makes me prefer ext3 over NTFS.

---

### Post by Yoooder on 2007-08-17
> **kellemes said:**
> There are a lot of filesystems to consider, including ntfs, etx2/3, reiser etc..
It's much too complicated for me to understand, so for sharing I always use FAT32, it works great.

Yech, Fat's only acceptable home is on a flash drive anymore.  Not going into details, but just trust that you'd be in better shape with ext2/3 and a windows driver

---

### Post by Sbarton on 2007-08-17
venerence, the google was a suggestion, I am pleased to see you tried it!.
regards

---

### Post by atlfalcons866 on 2007-08-19
ext3 does fragment 

Log of fsck -C -R -A -a -f 
Sun Aug 19 14:49:42 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/sda2: 3354/17956864 files** (10.0% non-contiguous)**, 760488/35897242 blocks

Sun Aug 19 14:50:57 2007
----------------

(10.0% non-contiguous) also means 10% file fragmentation

---

### Post by jrusso2 on 2007-08-19
10% fragmentation will not cause performance problems.

---

