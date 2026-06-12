---
title: "NTFS or FAT32"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by wadeall on 2007-05-14
Last time I tried Linux the file format or my windows media partitions was an issue and i made most of my Windows partitions FAT32 so I could use them with both Windows and Linux.  I'm now trying a Feisty dual boot and it seems that the NTFS issue has gone away as some clever person has managed to get read and write working on Linux.  is this correct?  Can I convert my FAT32 partitions into NTFS now without worrying about the impact when I am using Linux or  is it better to reatin the partitions in FAT32 format for some reason?

Thanks

Wade

---

### Post by Cypher on 2007-05-14
Yes, "ntfs-3g" will allow you to access the data on the NTFS partition without any problems..

---

### Post by gigaferz on 2007-05-14
[https://launchpad.net/ntfs-config](https://launchpad.net/ntfs-config)

I got ubuntu ultimate edition, at it comes with this tool.

I ve only used twice  (to delete and save some files), and it works, but i was scared to use it because i think it might mess up your windows partition.

I think there is something else around there. check the unoficial ubuntu guide.

Honestly I think is a "use it at your own risk" deal.

---

