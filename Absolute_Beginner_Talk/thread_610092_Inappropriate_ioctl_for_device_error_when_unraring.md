---
title: "Inappropriate ioctl for device error when unraring"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by hotweiss on 2007-11-11
> Write error in the file /home/***/Desktop/***.ISO [R]etry, [A]bort
Write error in the file /home/***/Desktop/***.ISO
Inappropriate ioctl for device

I've now tried extracting a few other rar files so the problem isn't a corrupt file. This has happened all of a sudden and I was able to extract files before. Any ideas?

---

### Post by dharmagio on 2008-04-10
hi
i have the same problem
i think is related too some upgrade
because i was able to extract files and due to the last upgrade i cant

---

### Post by auraithx on 2008-05-22
Hey - I got this error when my drive was full.

This might fix it also

> sudo rm /usr/bin/unrar
sudo apt-get remove rar
sudo apt-get update
sudo apt-get install unrar

---

