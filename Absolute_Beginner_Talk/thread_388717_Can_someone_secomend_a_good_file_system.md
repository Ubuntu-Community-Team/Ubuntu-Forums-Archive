---
title: "Can someone secomend a good file system?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Maxbowd on 2007-03-19
Hello people,
I have been a regular user of ubuntu for about a year, i am now looking at setting up a dual boot system with windows XP, i would like to have a partition on my hard disk that can be acessed by both linux and windows opertaing systems. I was thinking about FAT 32, but was wondering if anyone could recommend alternatives which would allow easy read / write acess from both OSes?

---

### Post by etank on 2007-03-19
FAT32 would probably be best for what you are wanting to do. There has been some progress in NTFS write ability with apps like ntfs-3g but it is still possible to cause errors on the system.

---

### Post by Maxbowd on 2007-03-19
I was also wondering about the ability of windows to read linux type partitions, could it be done? Just asking out of curiosity really.

---

### Post by Kateikyoushi on 2007-03-19
I know a total commander plugin that can read reiser, and of course you have the extdriver for windows. [LINK]("http://www.fs-driver.org/")

---

### Post by konungursvia on 2007-03-19
Go with fat32 if it's just for your songs. If you're doing HD movies, go with ntfs or reiser (and downlaod the extensions that let both systems read each others' types). Fat32 file systems only allow maximum 4 GB per file, whereas some hi-def movies are 5-10 GB typically.

---

