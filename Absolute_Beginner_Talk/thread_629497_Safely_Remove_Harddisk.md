---
title: "Safely Remove Harddisk"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by vsugadhan on 2007-12-02
I cannot eject my external HDD safely. Every time i try to eject, i displays an error message...and auto detects the drive again opening windows!
I read somewhere in the forum that this is an error in feisty. Is there a workaround?

---

### Post by Dr Small on 2007-12-02
Could you please post the error message, or a screenshot so we could read what the error is ?

---

### Post by vsugadhan on 2007-12-02
It says " Cannot Eject Volume"
I have partioned the HDD into two, if it makes any difference....

---

### Post by gn2 on 2007-12-02
Have you unmounted both partitions first?

---

### Post by vsugadhan on 2007-12-02
It doesn't matter if I try to remove both or one. If i remove one, it gets detected again instantly. Same with removing both.

---

### Post by Dr Small on 2007-12-02
Hmm. What filesytem is the drive?
If I plug in my flash memory card (for my camera) and try to remove it, it won't let me unmount it either, so I have to end up just pulling it out, and it never resulted in any data loss.

Dr Small

---

### Post by vsugadhan on 2007-12-02
File system is FAT32. Yea it has never resulted in data loss, still everytime i remove, an error message pops up. So was wondering if it is possible to rectify the error.

---

### Post by deepjaju on 2007-12-03
same here dude.. wvwn my harddisk doesn eject.. have to just plug it out.. i have a 40 gb external hdd.. have fat32 partition... two partitions.. help !!

---

### Post by vsugadhan on 2007-12-03
Well no1 has an answer?

---

### Post by philinux on 2007-12-03
Have you tried unmount rather than eject

---

### Post by vanadium on 2007-12-03
This is indeed a Feisty bug (was it ever fixed?) A workaround is to move away

/usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi

After that, the right-click eject command changes to an unmount command, and the drive will be unmounted without problems. By the way, in Gutsy it is by default an unmount command.

---

### Post by vsugadhan on 2007-12-03
Yes, have tried that too with the same effect.

---

