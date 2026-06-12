---
title: "resizing partitions"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2006-12-29
i have ubuntu 6.10 amd64 installed and am using qtparted how do i resize my fat32 partion with it??? when i open it it has a box that comes up saying:

no device found. maybe your not using root user?

i ok that box and the program come up with nothing in it


what do i do/???


thanks in advance

---

### Post by az on 2006-12-29
You must be root (or have admin priviledges) to run qtparted.  The whole hard drive on which you are working needs to be unmounted as well.  Use sudo:

sudo qtparted


I suggest using the live cd since you can unmount every partition on the disk (including swap) and then work on it.

---

