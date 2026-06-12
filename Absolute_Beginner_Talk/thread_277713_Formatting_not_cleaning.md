---
title: "Formatting not cleaning"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Ack99 on 2006-10-15
When I try reformatting my hdd (which has a non-working Windows XP) using cfdisk or fdisk I can't erase the data, only change the filesystem.

---

### Post by Kateikyoushi on 2006-10-15
Use the mkfs.ext3 command to create the filesystem. [HOWTO]("http://www.idevelopment.info/data/Unix/Linux/LINUX_PartitioningandFormattingSecondHardDrive_ext3.shtml").

---

### Post by nudnik on 2006-10-15
> **Ack99 said:**
> When I try reformatting my hdd (which has a non-working Windows XP) using cfdisk or fdisk I can't erase the data, only change the filesystem.

If you want to wipe the disk clean, which is neccessary sometimes for a good install, I reccomend KillDisk, a free download from Active software. This is a DOS program which boots from either a floppy or a CD. 

The process takes a while, but I cant think of another program as thorough and easy to use.

---

