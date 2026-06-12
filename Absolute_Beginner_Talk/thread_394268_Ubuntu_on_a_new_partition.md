---
title: "Ubuntu on a new partition"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by govthos on 2007-03-26
I already have a partition (not my windows partition) I would like to use, will it recognize my windows install without going through the resize process?

In other words I have a 15GB partition for windows and a 40GB partition that has nothing on it. I would like to install ubuntu on a 14GB partition, have a 1GB swap and still have 25GB for storage. Would I be able to install ubuntu as my system is configured, and still be able to use XP. Or, does ubuntu only recognize a windows partition if it resizes the partition it is on.

Thank you for any advise you can give.

---

### Post by steve.horsley on 2007-03-26
First, use the windows disk manager to delete that unused partition. 
Then run the Ubuntu installer, telling it to install into the unused space on the disk. This allows the installer to create and format the partitions it wants. It is is far the easiest way. Installing into an existing partition involves using the custom partitioner which can be a bit daunting and has many opportunities for mistakes, on top of which you forgot to create a swap partition.

---

### Post by govthos on 2007-03-26
Just to make sure, I will be able to still use my windows installation without reinstalling.

Thank you for the advice.

---

### Post by steve.horsley on 2007-03-28
That's the intention, and I've done it that way several times.. There is always a slim chance that something will go wrong though, so do backups first, same as you would before a windows upgrade.

---

