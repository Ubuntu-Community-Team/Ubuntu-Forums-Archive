---
title: "Resizing my Linux partition"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2007-12-15
When I installed Linux, I wanted to do things the "right way" and have several partitions. Specifically I wanted /, /home, and /usr. But I had some problems, got frustrated and made one big partition.

Question 1: If I resize the partition, will I lose any information?

Question 2: If I create a new partition and put it to /home, for example, will I lose the stuff I have saved in /home?

Question 3: How do you make a partition have a certain directory tied to it? (Is that what 'mounting' means?)

---

### Post by dcstar on 2007-12-15
> **EmosSuck777 said:**
> When I installed Linux, I wanted to do things the "right way" and have several partitions. Specifically I wanted /, /home, and /usr. But I had some problems, got frustrated and made one big partition.

Question 1: If I resize the partition, will I lose any information?

Question 2: If I create a new partition and put it to /home, for example, will I lose the stuff I have saved in /home?

Question 3: How do you make a partition have a certain directory tied to it? (Is that what 'mounting' means?)

There are various HOWTOs in the forum with step-by-step instructions for exactly your situation, do a search and pick out one that you can use.

For a quick response:

1/ Only if something goes wrong (rare but possible)

2/ No, because you will be able to copy all the old data.

3/ Refer to the HOWTOs, and yes.

---

### Post by Pumalite on 2007-12-15
1.-Backup before resizing
2.-http://www.psychocats.net/ubuntu/separatehome
3.-sudo mkdir /media/disk
sudo mount -t ext3 /dev/xxx /media/disk
(replace ext3 for ntfs if that's the format)
(xxx you can find out with: sudo fdisk -lu)
(use Gparted Live CD to resize)

---

### Post by Pogeymanz on 2007-12-15
Cool. Thanks!

---

### Post by Pumalite on 2007-12-15
Good luck!

---

