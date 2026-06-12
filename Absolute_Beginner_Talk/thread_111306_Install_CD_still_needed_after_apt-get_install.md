---
title: "Install CD still needed after apt-get install"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by stroopwafel on 2006-01-02
I think that my install CD did not get copied onto the HD during installation, because after doing a ```
sudo apt-get install bluefish
```I was prompted to insert my install CD.

How can I redo this installation step of copying my installation CD (Ubuntu 5.10) to the HD?

---

### Post by mazelado on 2006-01-02
I'm not exactly sure why, but this is normal behavior. There are some packages that get copied off the CD instead of from a repository. You don't need to redo anything.

---

### Post by meborc on 2006-01-02
but after u have installed it from the install cd, do **apt-get update **and then **apt-get upgrade**... i believe that there should be a newer version of bluefish in extra repositories or backports... for the best **sources.list** try to search the forums... i'm not in my ubuntu box so i cant tell you what i have there... good luck:)

---

### Post by xmastree on 2006-01-02
All you need to do is remove (or comment) the Install CD in your /etc/apt/sources.list (should be the first entry) and you won't be asked for the CD again. Packages will be downloaded from the net instead.

---

### Post by stroopwafel on 2006-01-02
[QUOTE=meborc]but after u have installed it from the install cd, do **apt-get update **and then **apt-get upgrade**... i believe that there should be a newer version of bluefish in extra repositories or backports... for the best **sources.list** try to search the forums... i'm not in my ubuntu box so i cant tell you what i have there... good luck:)[/QUOTE]
I did the update and upgrade. Now Bluefish can't find the PHP reference. I know this is not a bluefish forum, but what am I missing to browse the PHP reference in BLue fish?

---

