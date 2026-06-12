---
title: "How to mount my Windows Partition"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by comppsyco on 2006-08-30
Hello All,
I'm a somewhat noobie, and I have no idea how to go about mounting my Windows  partition. I have two HDs in my computer, one 120GB and the other 40GB. Ubuntu is installed on the 40gig one, and Windows is on an 90GB partition on the other one. Not only would I like to mount my Windows (ntfs) partition, I would also like to be able to use the extra 30GB as shared storage between the OSs.

---

### Post by Abstract on 2006-08-30
Try reading this in the wiki to mount NTFS:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

In order to have a shared partition you'll need to format it as FAT32 or use buggy NTFS writing. The previous link explains FAT32, NTFS writing is here:

[https://wiki.ubuntu.com/Lkraider/NtfsFuse](https://wiki.ubuntu.com/Lkraider/NtfsFuse)

Also, note that you can read NTFS by default in Dapper. You don't need Fuse to read NTFS.

---

### Post by comppsyco on 2006-08-31
How do I format that to Fat32? I don't even know what it is right now.

---

### Post by omns on 2006-08-31
.

---

