---
title: "formatting NTFS partitions"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2006-10-16
Cheers,

I have an NTFS partition that is mounted using ntfs-3g now that I have already copied all the contents of that partition I wanted to format it and make it a linux partition.  My question is how do I this? what steps should I take?

Also, is there a tool like Partition Magic that will convert a partitions file system from one to another without removing the existing data?  This is because I still have another NTFS drive that I would love to convert into a Linux one but I just dont have enough resource on me to backup the data.

thanks

---

### Post by wieman01 on 2006-10-16
As for the tool I would opt for **[COLOR="Red"]"gparted"[/COLOR]** which you can install from the repository. However, I am afraid that you won't be able to convert a NTFS/FAT32 partition into a Linux file system. 

In order to format the partition in question (and consequently erasing all data on it) you need to unmount it & use GParted to format it.

---

### Post by jd65pl on 2006-10-16
If you have an Ubuntu live CD you could boot using the CD and format the partition (thus loosing all information on the partition) using gparted on there as the partition should not be mounted.

---

### Post by delphiguy on 2006-10-16
Thanks for the help guys, gParted did indeed do the trick

---

