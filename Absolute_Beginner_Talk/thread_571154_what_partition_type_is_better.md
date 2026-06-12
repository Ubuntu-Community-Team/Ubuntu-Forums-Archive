---
title: "what partition type is better?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-10-06
I've always wondered about why there are so many unix filesystems, but more importantly, why!  And how is each one better or worse than another!?

I'm mainly looking for an explanation on the following (don't leave out even the most (what you think are) basic details! :p)

**ext3**, **ext2**, **reiser4**, **reiserfs** and _*any other versions of **reiser** and/or **ext***_

:confused:

(about the poll - I apologize if some of them don't exist :p)

---

### Post by rsambuca on 2007-10-06
[http://en.wikipedia.org/wiki/File_system](http://en.wikipedia.org/wiki/File_system)

---

### Post by ryanVickers on 2007-10-06
Ok, but that doesn't seem to really explain the difference between such specifics like ext and reiser...

---

### Post by rsambuca on 2007-10-06
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

---

### Post by bodhi.zazen on 2007-10-06
Thread moved as it is not a (direct) request for support.

I have used all of these, and, IMO I did not see much of a performance boot on day-to-day activity between the various file systems.

I have settled into ext3 as, in the end, I opted for stability over performance. You need to be careful with some of these file systems in that some are more vulnerable to power outages, notably JFS and XFS (although all are vulnerable to some extent).

Just a heads up that speed on the various "benchmark tests" is only one of many considerations.

Here is a very nice summary : [http://infohost.nmt.edu/~val/review/choosing.pdf](http://infohost.nmt.edu/~val/review/choosing.pdf)

It is a PDF and it reviews a number of additional issues/concerns.

---

### Post by D-EJ915 on 2007-10-06
I use JFS on all my systems, never had a problem.  I remember reading that it was best with dealing with lots of small files which I always have a ton of so that's the reason why I chose it, mainly.

From that review, I'm not surprised that XFS is the best at dealing with large files as SGI created it specifically to deal with large media files with IRIX.

---

### Post by Rhapsody on 2007-10-06
I had no idea which file system to use when I started using Linux, so I did the sensible thing and used ext3. I've had opportunities to switch since then, but I haven't since I've decided that the stability and reliability of ext3 are worth the relatively minor performance concerns. I'll probably move to ext4 once it's stable enough.

Additionally, the poll seems rather odd in that ext (which hasn't been supported in Linux since kernel version 2.1.21) and Reiser 1/2 (do they even exist as public releases?) are included while more commonly used file systems like JFS and XFS were left out.

---

### Post by K.Mandla on 2007-10-06
I just stick with ext2. Never had a problem, and I can't say the same for other filesystems I've tried. ... :(

---

### Post by regomodo on 2007-10-06
xfs

---

### Post by stimpack on 2007-10-06
Tried to use XFS and JFS on a removable drive but it failed to automount (not a problem with the FS, somthing in Ubuntu). So I don't know about them.

Only tried ext3 and ReiserFS. ext3 does a filesystem check every 20 boots, so it had to go, ReiserFS now.

---

### Post by atlfalcons866 on 2007-10-06
ext3- pretty stable long fsck. It is also one of the slower filesystems. It dosent have dynmaic i-node allocation. I use it because its the default fs in ubuntu and it hasnt corrupted on me on a power outage, I would rather have my files safe then being faster.

Resiserfs- never used

XFS- corrupted on a power outage on me. 

JFS- I never had a problem with jfs. Its fast and has dynamc i-node allocation but the dynamic i-node allocation means the inodes could be anywhere on the hard disk and slow down. JFS also seems to fragment fast even though it uses extents.

---

### Post by ryanVickers on 2007-10-06
interesting...

---

### Post by HermanAB on 2007-10-06
Hmm, Ext3 was designed as a transparent upgrade to Ext2.  It is excellent for that purpose, but I don't think that one should use it for a fresh install.  The reason being that it is extremely wasteful with disk space.  I think it is extremely unfortunate that Ext3 is the default for RedHat and Ubuntu systems, unless of course if you happen to own Seagate stock.

Ext3 has about 7.5% overhead and in practice use much more space than any other journaled FS.  On a small business server, Ext3 can easily use twice the amount of disk space to store a set of files than ReiserFS.  This is from my own experience when upgrading servers.

ReiserFS is now unmaintained, so my new favourite is JFS which has overhead of less than half a percent.  XFS had some bad bugs recently, so I still avoid it.

---

### Post by atlfalcons866 on 2007-10-06
jfs isnt supported anymore. EXT3 reserves 5% for inodes.

---

### Post by jrusso2 on 2007-10-06
Lately I have been playing around with JFS and I use XFS for the large storage partitions.

---

### Post by jrusso2 on 2007-10-06
> **atlfalcons866 said:**
> jfs isnt supported anymore. EXT3 reserves 5% for inodes.

Who said JFS is not supported anymore?  Got a link?

---

### Post by jrusso2 on 2007-10-06
> **HermanAB said:**
>  ReiserFS is now unmaintained, so my new favourite is JFS which has overhead of less than half a percent.  XFS had some bad bugs recently, so I still avoid it.


Who says Reiser is unmaintained?

[http://www.namesys.com/](http://www.namesys.com/)

---

### Post by atlfalcons866 on 2007-10-06
in this pdf file

[http://infohost.nmt.edu/~val/review/choosing.pdf](http://infohost.nmt.edu/~val/review/choosing.pdf)

---

### Post by atlfalcons866 on 2007-10-06
> **jrusso2 said:**
> Who says Reiser is unmaintained?

[http://www.namesys.com/](http://www.namesys.com/)

Hans reisier got arrested the future of reiser is uncertain
[http://en.wikipedia.org/wiki/Hans_Reiser](http://en.wikipedia.org/wiki/Hans_Reiser)

---

### Post by ryanVickers on 2007-10-06
> **atlfalcons866 said:**
> in this pdf file

[http://infohost.nmt.edu/~val/review/choosing.pdf]("http://infohost.nmt.edu/%7Eval/review/choosing.pdf")

Thanks - that especially, plus all these comments have helped clear things up :)

---

### Post by jrusso2 on 2007-10-06
> **atlfalcons866 said:**
> Hans reisier got arrested the future of reiser is uncertain
[http://en.wikipedia.org/wiki/Hans_Reiser](http://en.wikipedia.org/wiki/Hans_Reiser)

Namesys will maintain Resier FS.  As long as they are in business Resier will have a place.

---

### Post by Erunno on 2007-10-06
I use XFS mostly due to the reason that it comes with an online defragmentation tool (yes, even Linux file systems suffer from fragmentation that's why ext4 will have an defragmentation utility as well) and I tend to keep some partitions a long time around.

ext3 can also suffer damaged data when it's mounted with the writeback option but that's not the default in any distribution I know of. Since my notebook comes with a built-in UPS the only thing I have to fear are kernel panics.

---

### Post by atlfalcons866 on 2007-10-06
The default journal option in ext3 is jorunal data ordered There are 3 diffrent modes for ext3 journal mode they are jorunal writeback jorunal data and jorunal data ordered

Journal 
    (slow, but least risky) Both metadata and file contents are written to the journal before being committed to the main filesystem. This improves reliability at a performance penalty because all data has to be written twice. Without this setting in /etc/fstab, a file being edited in-place during a power outage or kernel panic risks being corrupted, depending on how the application is writing to the file.
Ordered 
    (medium speed, medium risk) Ordered is as with writeback, but forces file contents to be written before its associated metadata is marked as committed in the journal. This is the default on many Linux distributions.
Writeback 
    (fastest, most risky; equivalent to ext2 in some sense) Here metadata is journaled but file contents are not. This is faster, but introduces the hazard of out-of-order writes where, for example, files being appended to during a crash may gain a tail of garbage on the next mount.

---

### Post by atlfalcons866 on 2007-10-06
Disadvantages for ext3

[edit] Functionality

Since ext3 aims at being mostly compatible with ext2, many of the on-disk structures are similar to those of ext2. Because of that, ext3 lacks a number of features of more recent designs, such as dynamic allocation of i-nodes and variable block sizes (frags or tails).

ext3 filesystems cannot be fscked while the filesystem is mounted for writing. A dump of the filesystem taken while it is mounted read-write may result in corrupt data within the dump file.

ext3 does not support extents, a feature found in other filesystems such as JFS2 and ext4.

[edit] Defragmentation

There is no online ext3 defragmentation tool working on the filesystem level. An offline ext2 defragmenter, e2defrag, exists but requires that the ext3 filesystem be converted back to ext2 first. But depending on the feature bits turned on the filesystem, e2defrag may destroy data; it does not know how to treat many of the newer ext3 features.[4]

There are userspace defragmentation tools like Shake[2] and defrag[3], which work by copying each file and hoping the newly allocated file was not fragmented. However this only works if the filesystem is reasonably empty, and such filesystems are not usually fragmented. A true defragmentation tool does not exist for ext3 [4].

[edit] Undeletion

Unlike ext2, ext3 zeroes out block pointers in the inodes of deleted files. It does this to simplify read-write access to the filesystem when the journal is being replayed after an unclean mount. This, however, effectively prevents files from being undeleted. The user's only recourse is to grep the hard drive for data known to signal the start and end of the file. This provides slightly more secure deletion than ext2, which can be either an advantage or a disadvantage.

[edit] Compression

Support for transparent compression (available as an unofficial patch for ext2) is not available in ext3.

[edit] Size limits

ext3 has a relatively small maximum size for both individual files and the entire filesystem. These limits are dependent on the block size of the filesystem; the following chart summarizes the limits[5]:
Block size 	Max file size 	Max filesystem size
1KiB 	16GiB 	2TiB
2KiB 	256GiB 	8TiB
4KiB 	2TiB 	16TiB
8KiB 	16TiB 	32TiB

The 8KiB block size is only available on architectures which allow 8 KiB pages (such as alpha).

---

### Post by atlfalcons866 on 2007-10-06
Criticism of ResiserFS

Some directory operations (including unlink(2)) are not synchronous on ReiserFS, which can result in data corruption with applications relying heavily on file-based locks (such as mail transfer agents qmail[5] and Postfix[6]) if the machine halts before it has synchronized the disk.[7]

There are no programs to specifically defragment a ReiserFS file system, although tools have been written to automatically copy the contents of fragmented files hoping that more contiguous blocks of free space can be found. However, Reiser4 will have a repacker that optimizes file fragmentation.[8]

[edit] fsck

The tree rebuild process of ReiserFS's fsck has attracted much criticism: If the file system becomes so badly corrupt that its internal tree is unusable, performing a tree rebuild operation may further corrupt existing files or introduce new entries with unexpected contents [9]. But this action is not part of normal operation or a normal file system check and has to be explicitly initiated and confirmed by the administrator.

Nevertheless it is recommended not to store ReiserFS v3 images on a ReiserFS v3 partition (e.g. backups or disk images for emulators) without transforming them to a form that avoids misleading the file system, e.g., by compressing or encrypting. Reformatting an existing ReiserFS v3 partition can also leave behind data that could confuse the rebuild operation and make files from the old system reappear. This also allows malicious users to intentionally store files that will confuse the rebuilder. As the metadata is always in a consistent state after a file system check, corruption here means that contents of files are merged in unexpected ways with the contained file system's metadata. The ReiserFS successor, Reiser4, fixes this problem.

[edit] Earlier issues

ReiserFS in versions of the Linux kernel before 2.4.16 were considered unstable by Namesys and not recommended for production use, especially in conjunction with NFS.[10]

Early implementations of ReiserFS (prior to that in Linux 2.6.2) were also susceptible to out-of-order write hazards. For example, files being appended to during a crash gained a tail of garbage upon next mount.[citation needed] But the current journaling implementation in ReiserFS is now on par with that of ext3's "ordered" journaling level.

---

### Post by LaRoza on 2007-10-06
NTFS, I like that it needs me whereas the others like EXT3 work fine without my help. I like tending to NTFS and working with its quirks and complaints.

In seriousness, I use EXT3 and FAT32 most of the time. EXT3 for it widespread support and stability and FA32 for its use in any environment, despite its faults and limitations.

---

### Post by -grubby on 2007-10-07
I've only used EXT2 and EXT3 and I honestly can't tell the difference.

---

### Post by coront on 2007-10-09
ext2 or ext3 ? :)

---

### Post by coront on 2007-10-09
I meant filesystem sorry

---

### Post by Whiffle on 2007-10-09
ext3 is basically a more developed version of ext2.  It journals and has some other features that are quite useful.  Heres some good info:

[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

### Post by bodhi.zazen on 2007-10-09
There is a discussion of similar issues here (thread merged).

---

