---
title: "Partition Question What file Format ?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by victorash on 2007-04-25
Im planning to install Ubuntu 7.04 on my system Im running Windows XP and will set it up as a Dual Boot, I have decided to partition my drive and will allow 50Gb for Ubuntu. But my question is when I tried to partition my drive it asks what File system I want to select for the Partition, the list is – NTFS, Fat32, Ext2, Ext3, Reiser FS, Linux Swap, None, I Know its not the NTFS But a few of them mention Linux. I just want let Linux set it self up and it can use the 50Gb as it wants.  

 Thanks Alan

---

### Post by Bachstelze on 2007-04-25
You don't need to create the partitions for Ubuntu, this will be done during installation.

---

### Post by Parmenion on 2007-04-25
Well, you could use ext2, ext3, reiserfs as your file system. Linux swap refers to a defined virtual memory space on your drive. Its better to use the guided partioner in your case.

---

### Post by alienexplorers on 2007-04-25
Select the ext3 format for the ubuntu partition.  Remember to leave a small partition as the Ubuntu swap partition.

---

### Post by mac.ryan on 2007-04-25
As pointed out by somebody already ext3 is a good - all purposes - choice. You should however be aware that different filesystems have different features, pros and cons.

For example: ext3 has a journaling system that ext2 doesn't: this makes your files much safer. ReiserFS is dramatically faster than ext3 in certain given conditions (typically plenty of very small files...), fat32 is natively supported by both Windows and Linux (so that it is possible to share data between the two, if you need that feature), NTFS is being supported only since a few months, etc, etc...

---

### Post by az on 2007-04-25
Just leave it as free space (without a filesystem).  The Ubuntu installer will use that space to create the root and swap partitions for you.  No need to do anything.  You don't have to worry about how big to make your swap, and so forth.

As stated, you could just forget doing it yourself and boot the Ubuntu installer.  It can safely and easily shrink your current windows partition for you.  It will offer to do this by default, in fact.

---

