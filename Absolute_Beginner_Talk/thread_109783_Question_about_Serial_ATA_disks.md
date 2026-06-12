---
title: "Question about Serial ATA disks"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by juiced on 2005-12-29
I've got a little question,
i have 3 disks in my computer who are all serial ata.
most of those disks are in ntfs format cause they contain my data i used in windows.
Now i want to access this data also in linux, but everytime i try to acces one of those disks (who i can see on my desktop) he states "u don't have the rights to see this data".

Does anyone knows what i have to do??

thx in advance

Juiced

---

### Post by FlyDoc on 2005-12-29
Read this:

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions)

Option umask=0222 is the important thing, and it allows users other than root to access ntfs partition.

---

### Post by juiced on 2005-12-29
thx

---

