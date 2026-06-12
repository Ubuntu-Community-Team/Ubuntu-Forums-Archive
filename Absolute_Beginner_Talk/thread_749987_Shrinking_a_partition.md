---
title: "Shrinking a partition?"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by dreadh3ad on 2008-04-09
I need to shrink my windows partition.  I have performed a scan disk and a defrag.  I will be using gparted to shrink the partition.  If you look at the picture below you will notice that the free space is decentralized and there is a large block of contiguous files.  How will gparted shrink this partition?  Will it move the contiguous files or delete them?

[http://img384.imageshack.us/img384/9540/hdml4.jpg](http://img384.imageshack.us/img384/9540/hdml4.jpg)

---

### Post by metalf8801 on 2008-04-09
I have had problem shrinking a windows partition using gparted so back thing up first.  Also you might what to defrag first.

---

### Post by swoll1980 on 2008-04-09
mine have always looked like that it doesn't matter either those arent acurate or gparted fixes it automaticly either way its nothing to worry about you should still backup though

---

### Post by Tatty on 2008-04-09
Agreed, back up anything important, but dont worry too much.

Though i would recommend defragging a couple more times.  Three defrags is usually a good number before a partition resize.  I can even see some fragmented files showing in that screenshot.

---

### Post by dreadh3ad on 2008-04-09
Gparted refuses to mount my hard drive.  It just sits there for a good 20 minutes doing nothing.

---

### Post by Tatty on 2008-04-09
> **dreadh3ad said:**
> Gparted refuses to mount my hard drive.  It just sits there for a good 20 minutes doing nothing.

Your hard drive has to be unmounted before you can edit the partitions...

---

### Post by cotcot on 2008-04-09
A partition needs to be unmounted to be shrinked.
Try the Gparted LiveCD.

---

