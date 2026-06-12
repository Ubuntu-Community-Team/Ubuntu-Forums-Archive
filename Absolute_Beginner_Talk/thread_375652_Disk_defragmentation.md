---
title: "Disk defragmentation?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-03-04
Is there a way to defragment your linux partitions?  Do ext3 partitions even need to be defragmented?

---

### Post by Maestro23 on 2007-03-04
> **Matt1632 said:**
> Is there a way to defragment your linux partitions?  Do ext3 partitions even need to be defragmented?

No need to defrag ext3 file systems.

---

### Post by yabbadabbadont on 2007-03-04
Yes.  Yes.

(Would you like to know how too?  :D)

There are various scripts and programs floating around in linux world for doing this task on ext2 and ext3 filesystems.  I think there is even a large thread here in the forums on this.

[http://www.ubuntuforums.org/showthread.php?t=169551](http://www.ubuntuforums.org/showthread.php?t=169551)

---

### Post by yabbadabbadont on 2007-03-04
> **Maestro23 said:**
> No need to defrag ext3 file systems.

Actually there is... sometimes.  I've got one filesytem that is 9 or 10 percent fragmented right now.   (as reported by fsck)

---

### Post by Kateikyoushi on 2007-03-04
No you don't really need to defragment it, but if you really want look here. [LINK]("http://en.wikipedia.org/wiki/Ext3")

---

### Post by Maestro23 on 2007-03-04
> **yabbadabbadont said:**
> Actually there is... sometimes.  I've got one filesytem that is 9 or 10 percent fragmented right now.   (as reported by fsck)

Not to the point of say an NTFS or FAT32 partiton.  Whatever works for ya man.:)

---

### Post by Matt1632 on 2007-03-04
Oh, ok. Thanks for the answers.

---

### Post by mcduck on 2007-03-04
> **yabbadabbadont said:**
> Actually there is... sometimes.  I've got one filesytem that is 9 or 10 percent fragmented right now.   (as reported by fsck)

Ext filesystems do get fragmentation, but it has no effect on performance as long as your disk isn't getting completely full. My external drive has now 18% fragmentation, but running some performance tests there is no difference compared to my main drive (with 0.2% fragmentation) :D

So there really is no need for defrag. Actually people have reported their drive performance to decrease after defragging Ext3..

---

### Post by yabbadabbadont on 2007-03-04
> **mcduck said:**
> Ext filesystems do get fragmentation, but it has no effect on performance as long as your disk isn't getting completely full. My external drive has now 18% fragmentation, but running some performance tests there is no difference compared to my main drive (with 0.2% fragmentation) :D

So there really is no need for defrag. Actually people have reported their drive performance to decrease after defragging Ext3..

Unfortunately, it is the full partitions that seem to always get fragmented...  :lol:

The best way that I've found to fix it is to backup, wipe the partition, then restore.

---

