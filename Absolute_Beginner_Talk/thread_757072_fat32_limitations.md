---
title: "fat32 limitations"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by waggingwabbit on 2008-04-16
i just looked at this site:

[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

if i want to dual boot and have a shared partition i have to use fat32? it says it has a 4gb file limit and files arent recoverable. what does this mean? when i delete files is it permanently gone? unrecoverable with recuva or something similar? is the deleted file really going to be deleted from the hard drive or will it still be in there marked as "empty or rewritable" but you just can't recover it? hope thats not too confusing to understand. those of you who know about recovering files please answer me :confused:

---

### Post by prshah on 2008-04-16
> **waggingwabbit said:**
> i just looked at this site:

if i want to dual boot and have a shared partition i have to use fat32? it says it has a 4gb file limit and files arent recoverable. what does this mean? when i delete files is it permanently gone? 

Yes, 4Gb is the FILE size limit on FAT32; that means that you can't store a full DVD ISO image; for example. (For nit pickers; 3.98 Gb)

Unless you use a third party utility to permanently "wipe" a file, files are _very_ much recoverable from a fat32 partition using any number of free, shareware and/or commercial utilities.

Further, in Windows XP, you cannot create a FAT32 partition of greater than size 32Gb. This seems to be an intentional limit. You can create larger than 32Gb partitions with other partitioning software including Gparted, PartitionMagic etc, which XP will happily play with. 

But if you're planning to use FAT32 to share a partition between Windows and Linux, that's no longer necessary since with 7.10 (Gutsy) NTFS read/write support is out of the box and stable.

And you can also access your linux partitions (not recommended, though) in Windows with the free IFS EXT2/3 driver from [www.fsdrivers.org](www.fsdrivers.org).

---

### Post by csi_ on 2008-04-16
> if i want to dual boot and have a shared partition i have to use fat32? 

You can choose between FAT32 and NTFS. Both will be read/write enabled.

> it says it has a 4gb file limit and files arent recoverable. what does this mean?

One file cannot oversize 4gb. Recoverable means it is kind of safer, I read it on the site your provided ([http://www.ntfs.com/data-integrity.htm](http://www.ntfs.com/data-integrity.htm))

also check: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?action=fullsearch&context=180&value=ntfs&titlesearch=Titles](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?action=fullsearch&context=180&value=ntfs&titlesearch=Titles)

---

### Post by waggingwabbit on 2008-04-16
oh.. o.o

so should i make a shared partition (ntfs instead of fat32) now that ntfs works with ubuntu?

that link ([http://www.ntfs.com/data-integrity.htm](http://www.ntfs.com/data-integrity.htm)) doesn't say anything about recorability in fat32...

---

### Post by prshah on 2008-04-16
> **waggingwabbit said:**
> 
so should i make a shared partition (ntfs instead of fat32) now that ntfs works with ubuntu?
that link ([http://www.ntfs.com/data-integrity.htm](http://www.ntfs.com/data-integrity.htm)) doesn't say anything about recorability in fat32...

There is no need to make a SEPARATE NTFS partition; Ubuntu can read/write to your existing NTFS partitions. If you want to though, yes, you can make a separate NTFS partition for shared files.

If the site recommends that you use a FAT32 partition for sharing files between ubuntu and windows, then it should be rather outdated, in my opinion; and thus I wouldn't put too much store by what's said there.

---

### Post by prshah on 2008-04-16
> **waggingwabbit said:**
> 
that link ([http://www.ntfs.com/data-integrity.htm](http://www.ntfs.com/data-integrity.htm)) doesn't say anything about recorability in fat32...

It talks about file system recoverability in case of a bad shutdown; has nothing to do with recovering deleted files.

---

