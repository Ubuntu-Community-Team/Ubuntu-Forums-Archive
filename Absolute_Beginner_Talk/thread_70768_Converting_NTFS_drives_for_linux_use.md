---
title: "Converting NTFS drives for linux use?"
date: 2005-10-01
forum: Absolute Beginner Talk
---

### Post by cafevincent on 2005-10-01
I've had it with Windows XP and I'm about to install Ubuntu (never used linux before) but there is a problem: I have approx. 1.2 terabytes of data on NTSF hard drives that need to remain writable (I understand this can't be done under linux) so I should probably just convert them because I don't plan to go back to Windows ever again, not even dual boot. I can convert to large FAT32 partitions with PartitionExpert but is this smart? FAT32 is a filesystem Linux can use perfectly right? Or is there another filesystem I should consider or anything else I should know?

---

### Post by Leif on 2005-10-01
fat32 is fine with linux, but make sure you backup everything before trying to convert.

---

### Post by cafevincent on 2005-10-01
I just realized there is some serious limitations in FAT32, most of my files are over 4GB and all of the partitions are over 128GB. FAT32 is therefore out of the question.

---

### Post by Leif on 2005-10-01
if you really don't intend to use windows anymore, why not go for ext3 or reiserfs ? actually, from what I've hear, xfs is great for large partitions. if you've got a decent amount of free space, you could resize your existing partitions, create a new linux partition, move your data over, then reduce the windows partition again, increase linux partition size again, move things over, and repeat till done.

or, in a less painful way, back everything up somewhere safe, delete the windows partition, create linux partition, unzip all backed up data.

---

### Post by cafevincent on 2005-10-01
[QUOTE=Leif]if you really don't intend to use windows anymore, why not go for ext3 or reiserfs ? actually, from what I've hear, xfs is great for large partitions. if you've got a decent amount of free space, you could resize your existing partitions, create a new linux partition, move your data over, then reduce the windows partition again, increase linux partition size again, move things over, and repeat till done.[/QUOTE]

Is there any way to convert NTFS to any of these filesystems? Resizing seems like a lot of work but I can do it for the one most important drive. I need to do this in linux right?

[QUOTE=Leif]or, in a less painful way, back everything up somewhere safe, delete the windows partition, create linux partition, unzip all backed up data.[/QUOTE]

That's impossible. I won't buy another terabyte to backup. Most of my files won't fit on single layer DVDs and a dual layer DVDs are way too expensive. Also I don't have the time to burn 250 DVDs.

---

### Post by Leif on 2005-10-07
I'm afraid I don't know of any utilities that will convert ntfs to ext3 or such, and I don't know of any other ways of getting what you need done.

---

