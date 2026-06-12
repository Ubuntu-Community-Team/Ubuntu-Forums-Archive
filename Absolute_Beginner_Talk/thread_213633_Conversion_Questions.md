---
title: "Conversion Questions"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by smurphv2 on 2006-07-11
Hey all,
    I am considering starting up a dual boot XP/Ubuntu system. Currently I am only running XP. I am familiar with linux, but only so much as using it, not configuring anything. I have a few questions regarding this process first.

1. In terms of file systems, what would be the best way to convert items to be able to be read/write between the two OSs. For example, I have a large partition (NTFS) that is filled with music ripped from my CD collection. Obviously, I'd like a partition that is accessible for read/write access in both OSs. Is the only reliable way to do this to create another partition that is FAT32, and then transfer all those files from the NTFS partition to the FAT32? Then in this way I would be able to read/write from that partition in either Windows or Ubuntu?

2. Is there an open source drive emulation program, similar to alcohol 120%, where you can create logical drives and then mount images to those drives?

Edit: after searching more heavily, I've found a thread which seems to offer a solution (for anyone else who may not know): [http://ubuntuforums.org/showthread.php?t=160355&highlight=alcohol+120](http://ubuntuforums.org/showthread.php?t=160355&highlight=alcohol+120) Still, it would be nice if there were a more intuitive approach.

I'm sure I'll have more questions, but this is all that I can think of to start off. Thanks in advance for any information you may provide.

---

### Post by DavidFL on 2006-07-11
> **smurphv2 said:**
> Hey all,
    I am considering starting up a dual boot XP/Ubuntu system. Currently I am only running XP. I am familiar with linux, but only so much as using it, not configuring anything. I have a few questions regarding this process first.

1. In terms of file systems, what would be the best way to convert items to be able to be read/write between the two OSs. For example, I have a large partition (NTFS) that is filled with music ripped from my CD collection. Obviously, I'd like a partition that is accessible for read/write access in both OSs. Is the only reliable way to do this to create another partition that is FAT32, and then transfer all those files from the NTFS partition to the FAT32? Then in this way I would be able to read/write from that partition in either Windows or Ubuntu?

2. Is there an open source drive emulation program, similar to alcohol 120%, where you can create logical drives and then mount images to those drives?

Edit: after searching more heavily, I've found a thread which seems to offer a solution (for anyone else who may not know): [http://ubuntuforums.org/showthread.php?t=160355&highlight=alcohol+120](http://ubuntuforums.org/showthread.php?t=160355&highlight=alcohol+120) Still, it would be nice if there were a more intuitive approach.

I'm sure I'll have more questions, but this is all that I can think of to start off. Thanks in advance for any information you may provide.

I'm not sure if you saw it but Ubuntu is able to read from NTFS partitions very well now. It is write support that is risky and not reccomended. So you could leave those files on your NTFS partition and at least be able to read from them still. :)  I ended up creating a fat32 partition (as you know of) and using that as a swap point.  I have read of a utility to mount linux ext3 partitions (as ext2) in windows somewhere on this forum but have not used it myself.  If that might help you may wish to search for this.

---

### Post by Zimmer on 2006-07-11
Dual boot info here that you may find helpful.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

