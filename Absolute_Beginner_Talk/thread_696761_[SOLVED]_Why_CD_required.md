---
title: "[SOLVED] Why CD required"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Faud on 2008-02-14
Why is 
```

sudo apt-get install build-essential

```
saying that it needs a CD ?

---

### Post by stevejesus on 2008-02-14
You need to disable the CD from your software sources.

Easiest way...  System > Admin > Software sources.  Find the CD-ROM and remove it.

---

### Post by PmDematagoda on 2008-02-14
That is because the repository for the installation CD is still there.

Open the sources.list file for editing using:-
```
sudo nano /etc/apt/sources.list
```

Then uncomment the entry for the CD-ROM by typing # in front of it, after that save the file and execute:-
```
sudo apt-get update
```
that should fix the problem.

---

### Post by Faud on 2008-02-14
many thanks, all fixed and thread marked as solved

---

