---
title: "root Drive is FULL"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2007-01-04
Hi when i go to gparted and show my drive status it shown my root drive which is 14 GB are totally (100%) Full and gDesklet shown its 10 GB free.:rolleyes:

---

### Post by energiya on 2007-01-04
Write in a terminal window "df -h" and see what its output is.

---

### Post by TLE on 2007-01-04
Open up a terminal and type
```
df -h
```
That'll tell you how much space you have on your partitions. BTW if your / partition really is full I recommend making some space before you shut down, otherwise you might only be able to boot in failsafe mode, and will have to clean the partition from the terminal. (I've tried it)
\TLE

---

### Post by bluefrog on 2007-01-04
sudo apt-get clean
will free some space by removing from apt's cache programs installation files not needed anymore as they are installed.

James

---

