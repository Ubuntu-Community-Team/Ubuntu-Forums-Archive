---
title: "Windows partitons? integrated partitions need space for dual boot ubuntu."
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Eldar11 on 2007-06-21
I'm working with a drive that have four partitons on it, two FAT16 partitons and two NTFS partitions.  I need to know how to move one or more of the FAT16 partitions into another partition so I can dual boot windows XP with Ubuntu.  I have Gparted, I dont know if it has that capability, but it would be nice to know.

---

### Post by EagleRock on 2007-06-21
I don't think you can "merge" FAT16 partitions.  You can try copying the data from one partition to the other, then deleting the one and expanding the other.  That might not be viable, however, depending on the space that's empty on both drives.  FAT16, luckily, will be easier than NTFS, since NTFS r/w support isn't automatically installed in Ubuntu (due to stability issues).

---

### Post by Eldar11 on 2007-06-21
see all thats on there right now is windows XP, I need to eliminate base partitons so I can install ubuntu, I read that you could put a partition within a partition, so I really have no idea.

---

### Post by Eldar11 on 2007-06-21
it's called an intergrated partition and thats what I need to figure out how to do.
[this]("http://en.wikipedia.org/wiki/Disk_partitioning#") is where I found the info and I was refered to that when trying to install ubuntu, by the installer, because the partition I was trying to install on couldn't be made, because there can be only 4 primary partitions.

---

### Post by Eldar11 on 2007-06-21
FAT16 is compatible with integrated partitons

---

