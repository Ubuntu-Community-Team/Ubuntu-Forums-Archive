---
title: "Defragment Question"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by zisme on 2006-08-03
Will that little bit of data get erased if I resize the partition? And if it will, how do I find out what data that is?
See attatched

---

### Post by calvinthomas on 2006-08-03
If you repartition and do not select to format then that bit of data will not be removed and will simply be where it is now, if you select to format then all of the data will be removed.

Calv

---

### Post by Tomosaur on 2006-08-03
It's always good practice to defragment before you perform any partition operations. There's no real easy way to find out what the information is. Your best bet is to just perform a defragmentation.

---

### Post by Lord Illidan on 2006-08-03
I believe that Windows stores multiple copies of some information, either the journal or boot information or both in different locations on the harddisk. (for redundancy) I believe what you are looking at is that information. If you resize the harddisk, then at bootup, XP should recreate that information.

---

### Post by zisme on 2006-08-03
Okay. Thanks for the info everyone!

---

### Post by az on 2006-08-03
> **zisme said:**
> Will that little bit of data get erased if I resize the partition? And if it will, how do I find out what data that is?
See attatched

It will not - parted or ntfstools will try to move it and if it can't do it safely, it will balk and do nothing.

---

### Post by zisme on 2006-08-03
Okay. That's even better to know. I'll try defrag once or twice more before I go to install (I can't yet, mom's making me wait for the CD's I ordered).

---

