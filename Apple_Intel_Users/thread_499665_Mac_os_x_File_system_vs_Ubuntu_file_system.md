---
title: "Mac os x File system vs Ubuntu file system"
date: 2007-07-12
forum: Apple Intel Users
---

### Post by Darth_Maul on 2007-07-12
Are the alike or different

---

### Post by thully on 2007-07-12
They're quite different.  Mac OS X uses the HFS+ file system, which itself is based on the HFS file system first used by Macs way back in 1985 or so.  Linux, on the other hand, generally uses the ext3 file system, which is based on the aptly-named ext2 file system used in the past on Linux. 

Both support many of the same features (like journaling for easy recovery from crashes), though the biggest difference is that HFS+ is traditionally case-insensitive (which means that test and Test are considered the same file), whereas ext3 and all other file systems used on Linux are case-sensitive (thus, test and Test would be different files).  You can have case-sensitive HFS+, though - it may be a good idea to use that for a partition if you're doing Unix development in OS X.  Also, on Linux there are other file systems besides ext3 - such as ReiserFS, XFS, and JFS, and the still-in-development ext4.

Because the file systems are different, there are some issues reading/writing OS X partitions from Linux (and vice-versa).  Linux supports HFS+, though it has read-write support only for NON-journaled HFS+ partitions (you can disable journalling in OS X).  OS X can support ext3, but you need to use a third-party driver.  Note that Linux doesn't have write support for UFS (an alternate file system for OS X and primary file system for BSDs) - if you want to share data, use non-journaled HFS+ (case-sensitive is OK, but not for a boot partition) or plain old FAT32.

Hope this answers your question :)

---

### Post by cyberdork33 on 2007-07-12
> **thully said:**
> They're quite different.  Mac OS X uses the HFS+ file system, which itself is based on the HFS file system first used by Macs way back in 1985 or so.  Linux, on the other hand, generally uses the ext3 file system, which is based on the aptly-named ext2 file system used in the past on Linux. 

Both support many of the same features (like journaling for easy recovery from crashes), though the biggest difference is that HFS+ is traditionally case-insensitive (which means that test and Test are considered the same file), whereas ext3 and all other file systems used on Linux are case-sensitive (thus, test and Test would be different files).  You can have case-sensitive HFS+, though - it may be a good idea to use that for a partition if you're doing Unix development in OS X.  Also, on Linux there are other file systems besides ext3 - such as ReiserFS, XFS, and JFS, and the still-in-development ext4.

Because the file systems are different, there are some issues reading/writing OS X partitions from Linux (and vice-versa).  Linux supports HFS+, though it has read-write support only for NON-journaled HFS+ partitions (you can disable journalling in OS X).  OS X can support ext3, but you need to use a third-party driver.  Note that Linux doesn't have write support for UFS (an alternate file system for OS X and primary file system for BSDs) - if you want to share data, use non-journaled HFS+ (case-sensitive is OK, but not for a boot partition) or plain old FAT32.

Hope this answers your question :)

Wow, good job. Very thorough.

---

### Post by Darth_Maul on 2007-07-12
Thanks what about the command line  creatting users  ect

---

