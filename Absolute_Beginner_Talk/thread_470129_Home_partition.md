---
title: "Home partition"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-06-10
I stupidly manage to delete all of my windows xp, and since i don't have an install cd i can't get it back (i was trying to change it from NTFS to FAT32 , but i didn't realise it would wipe all the data :(  )

Anyway, how can I now add some of this free space on as either a seperate home directory or just use it to make my existing home directory bigger without erasing any data on it?

---

### Post by tagra123 on 2007-06-10
Follow this guide and you should have no problems.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by floke on 2007-06-10
partition it as ext3, then mount the partition in your fstab as home; my fstab entry is:

/dev/sda6       /home   ext3    nodev,nosuid    0       2

This has some useful bits and pieces on it

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

