---
title: "Doubts regarding NTFS"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by jhwn on 2006-06-27
I've been reading a lot about this, and I think I know the answers, but I want to rest assured I'm not going to damage my NTFS partition.

Is it safe to copy files from a NTFS partition to an EXT3? I suppose it is, because the problem is writing on it, not reading from it.

Is it safe to share files stored in a NTFS partition with Nicotine?


And related, is there a way to shrink an EXT3 partition, to make room for another one, or a FAT32?

Thanks in advance. 

J

---

### Post by adam.tropics on 2006-06-27
[QUOTE=jhwn]I've been reading a lot about this, and I think I know the answers, but I want to rest assured I'm not going to damage my NTFS partition.

Is it safe to copy files from a NTFS partition to an EXT3? I suppose it is, because the problem is writing on it, not reading from it.

Is it safe to share files stored in a NTFS partition with Nicotine?


And related, is there a way to shrink an EXT3 partition, to make room for another one, or a FAT32?

Thanks in advance. 

J[/QUOTE]

On the first point, you sort of answered your own question! On Nicotine, I have not used it, but wouldn't envisage too many problems. That said, you would perhaps do better with a new partition you can write to simply as well. If you want to resize partitions from your current system, the easiest way, for me anyway, is to run the live cd. Then under System-->Administration you will find the disk partitioning tool (Called something like that). It has a fairly simple interface, and can resize partitions, as long as they are not mounted. On the live cd by default, I don't believe they are so that should be pretty straight forward. In the free space you create, you can make the new partition. Ext3 would be a good choice for that.

---

### Post by jhwn on 2006-06-27
Thanks adam.

I guess I got the answer, but being the GNUbie I am, I wanted to be assured. :D 


And I'll try resizing with the LiveCD, thanks again.

---

