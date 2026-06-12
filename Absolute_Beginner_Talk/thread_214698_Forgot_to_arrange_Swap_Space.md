---
title: "Forgot to arrange Swap Space"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by Captain Kirk76 on 2006-07-12
I forgot to give Ubuntu Swap space when installing, how badly will it affect my performance?
I have 512MB RAM

---

### Post by Captain Kirk76 on 2006-07-13
bump

---

### Post by kd7swh on 2006-07-13
It would be a big deal for some of the things I do. for most applications its no big deal but if you have some disk space for swap you can use "gpart" to make a swap partition from within ubuntu.

---

### Post by Captain Kirk76 on 2006-07-13
does swap space need t be in an empty Hard drive? i dont have space to partition another for it, and my other Hard drives are all FAT32 or NTFS

---

### Post by nanotube on 2006-07-13
swap space has to be a separate partition, although it can be on the same physical harddrive or on a different one, no matter.

if you do not do too much multitasking (running too many things at once), you can get by without a swap with 512m of ram, but you would do better to either find some space for a swap partition on one of your hds, or to get another stick of 512m ram (they are pretty cheap these days). :)

---

### Post by woedend on 2006-07-13
just use the ubuntu installer cd (alternate will at least, don't know so much about desktop) to resize your ubuntu partition enough to make a swap partition?
I do think you WILL need swap with 512 mb ram.  I have a gig and come into swap from time to time.

---

### Post by kigina on 2006-07-13
i have no swap and i do fine

---

### Post by Sef on 2006-07-13
You could also download [GParted]("http://gparted.sourceforge.net/livecd.php") to install the swap.  You should do 1 GB of swap.  (Swap should be double your ram, although if you have more than 1 GB of ram, you can usually do without it.)

---

### Post by Captain Kirk76 on 2006-07-13
How much Memory RAM does Ubuntu support (IE WIN XP supports up to 4GB)

---

### Post by nanotube on 2006-07-13
> **Captain Kirk76 said:**
> How much Memory RAM does Ubuntu support (IE WIN XP supports up to 4GB)

default kernel should support up to 4g, a custom-compiled one should be able to go up to 64g.

---

