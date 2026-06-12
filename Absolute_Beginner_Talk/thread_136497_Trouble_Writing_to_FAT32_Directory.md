---
title: "Trouble Writing to FAT32 Directory"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by tvanhuisen on 2006-02-26
Hi everyone,

I am working on completing my Ubuntu install and everything works pretty well except for one thing.

I am mounting two 125 GB FAT32 partitions on boot. Read and write access appears to be good from both my old XP install and in Ubuntu, however, I am unable to write to one of the directories on one of the partitions. The directory is a music directory filled with about 50 GB of music. There is another directory on the same mounted partition that contains a bunch of camera images and it seems to be fine.

I have read all of the information I could find on mounting FAT32 partitions in this forum and the wiki. I have tried a number of edits to the fstab file but I am still having problems with write permissions to this one directory. Any help would be appreciated.

---

### Post by localzuk on 2006-02-26
There could be a variety of issues. Can you access the directory from a different user in windows XP? If the folder belongs to a specific user in XP you may have permissions problems trying to write to it from any other user.

Try setting up a new user on the XP install and try and write into the directory from there. This will provide a little insight into the issue.

---

### Post by tvanhuisen on 2006-02-26
I just checked: multiple XP users are able to read/write to the music directory on that partition.

What is weird to me about this one is that the permission issue is only with one directory. The rest of the partition is fine.

---

### Post by tvanhuisen on 2006-02-27
Just to follow up: I was unable to address the permissions issue with the music directory, however, I was able to find a workaround. I just copied the directory contents to a new directory, deleted the problematic directory, and everything was fine.

I still do not know what the source of the permissions issue was but I can think of two reasons why it may have just been an XP issue. One, the directory and the files were written to the FAT32 partition from XP and, two, the directory contained DRM-protected music file from the iTunes music store.

---

