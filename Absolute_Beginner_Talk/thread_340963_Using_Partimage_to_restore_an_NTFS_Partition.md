---
title: "Using Partimage to restore an NTFS Partition"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by richmooremi on 2007-01-17
I recently used partimage to backup a clean NTFS Windows (because I'm a gamer) partition so that every time I need a fresh copy I won't have to reinstall and reconfigure everything, but I have a few questions:

1. Is the bzip2 compression setting likely to result in any errors, and is it wise to compress an NTFS partition this way?

2. After I restore the image, will I be able to boot to it as I do now?

3. (this may sound kind of dumb) Will I have to enable NTFS write support to restore the partition, or will partimage be able to reconstruct it bit by bit?

4. If not, can I copy the NTFS backup to a FAT32 partition (I'm almost certain I can't for one reason or another)?

5. Has anyone run into any problems doing this?

Thanks

---

### Post by aysiu on 2007-01-17
According to [PartImage's homepage](http://www.partimage.org/Main_Page): > **The NTFS (Windows NT File System) is currently not fully supported:** this means you will be able to save an NTFS partition if system files are not very fragmented, and if system files are not compressed. In this case, you will be able to save the partition into an image file, and you will be able to restore it after. If there is a problem when saving, an error message will be shown and you won't be able to continue. If you have successfully saved an NTFS NTFS partition, you shouldn't have problems as you restore it (except in the case of bugs). Then the best way is to try to save a partition to know if it is possible. If not, try to defragment it with diskeeper or another tool, and try to saving the partition again.

---

