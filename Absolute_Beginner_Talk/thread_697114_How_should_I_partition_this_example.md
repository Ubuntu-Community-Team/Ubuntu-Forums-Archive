---
title: "How should I partition this example?"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by TheSeb on 2008-02-14
First of all, this is not a general question... so please answer instead of pointing me to the general "how to partition" threads. And thanks ;)

So right now I have a clean out-of-box VISTA w/ _one_ 320 GB HD.

It is partitioned as follows (it came like that)

C: 29.3 GB - NTFS - Type: Basic
52% free
(Vista System Preinstalled on this drive)

D: 250.74 GB - NTFS (completley empty... but says 99% free)

OTHER: The remainder is reserved for backup settings by the manufactures and I want to make sure I don't mess with that by accident.

So what would you do with this setup to install ubuntu? I'd like to keep the Windows partition the way it is, and the hidden backup partition the way it is. Then, I'd like to make the 250GB one into a  Linux System partition and a general storage partition accessible by _both_ **Vista** and **Ubunutu** 

Something like this?

C: 29.3 GB - File System: NTFS - Type: Basic
52% free
(Vista System Preinstalled on this drive)

D: 50 GB Linux System HD - Type: ? File System: ?

E: 200GB - Type ? File System: ? (general storage for both systems)

OTHER: The remainder is reserved for backup settings by the manufactures and I want to make sure I don't mess with that by accident.


How big should the linux partition be, and also how should I format the new partitions? NTFS or something else... the new general storage partition MUST be usable by both systems.

---

### Post by jken146 on 2008-02-14
Replace your 250 GB empty NTFS partition with this:

A 10 GB ext3 partition for Ubuntu, mounted on /

A swap partition (size is RAM x 1.5, but not greater than 1 GB)

An NTFS partition for storage.  Mount this on /media/storage or some such.  This can take up all the remaining space.

---

### Post by TheSeb on 2008-02-14
> **jken146 said:**
> 
An NTFS partition for storage.  Mount this on /media/storage or some such.  This can take up all the remaining space.

I read somewhere that you should use FAT32 as opposed to partition to be able to use it with both Ubuntu and Windows... is that incorrect?

---

### Post by jken146 on 2008-02-14
You could use FAT32, but it is very disadvantaged compared to modern filesystems.  NFTS has read and write support in Linux, so you can use that.  There are also some Windows drivers that will let you use the ext3 filesystem to some degree ([http://fs-driver.org](http://fs-driver.org)).

---

