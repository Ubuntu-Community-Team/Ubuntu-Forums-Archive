---
title: "help with reformatting a second drive"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by yellowband on 2006-09-19
Hi

can somebody point me to a good tutorial that explains how to reformat a second hard drive with th ext3 filesystem, and how to mount it to use as a storage drive in a home sever?

basically i have my windows box that has 3 hard drives in it (2 of which are SATA and are for media storage).  I changed over to linux but the drives are still NTFS and i want to change that. i have my stuff backed up now i want to reformat the drives to a linux-type file system.  I have found this guide, but it is a bit over my head, especially the ext3 formatting part: [http://www.idevelopment.info/data/Unix/Linux/LINUX_PartitioningandFormattingSecondHardDrive_ext3.shtml](http://www.idevelopment.info/data/Unix/Linux/LINUX_PartitioningandFormattingSecondHardDrive_ext3.shtml)

thanks for any help.

---

### Post by bulldog on 2006-09-19
You should take a look at gparted.

Think what you want to do is perfectly possible with it.

I know no tutorials but do a search in the wiki,there should be some good stuff to read.

---

### Post by yellowband on 2006-09-19
cool. i think i figured most of what i needed.

one question though, can i mount two hard drives to the same directory?  i created a directory called /storage, and i want to mount both sdb and sdc there. can i do this? or do i need to creat two storage directories?

thanks.

---

