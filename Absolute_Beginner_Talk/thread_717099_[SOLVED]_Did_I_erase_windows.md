---
title: "[SOLVED] Did I erase windows?"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by philosophicscience on 2008-03-06
I recently installed ubuntu 7.10 on my acer aspire 5670. Going in, I followed a simple installation guide and was assured that installing ubuntu would allow me to dual boot. Just to be sure, I backed up my documents on an external and then used the live cd to install. However, I looked up examples of install options and for some reason mine only gave me 2 options. I picked the one that seemed least likely to erase all my stuff (i'm a casual gamer and enjoy having windows for that reason). 

Now however, grub doesn't show a window's XP option and I cannot find any of my old files anywhere on the machine. Help!

---

### Post by bodhi.zazen on 2008-03-06
please open a terminal and post the output of this command :

```
sudo fdisk -l
```

You can copy-paste from your terminal to here.

---

### Post by philosophicscience on 2008-03-06
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf8550f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

---

### Post by patrickaupperle on 2008-03-06
That looks almost exactly like mine. Unfortunately for you, I don't have windows.

---

### Post by Vadi on 2008-03-06
Less likely.. there was an option to use the entire drive, or a portion of it. Which did you pick?

---

### Post by halitech on 2008-03-06
Be thankful you backed stuff up, you just wiped windows out completely and only have Ubuntu.

---

### Post by CWaugh on 2008-03-06
When I installed Ubuntu to test it out, I confused the partition percentages and overwrote my XP install.  Maybe the same happened to you?  

I unfortunately didn't backup before installing.  I thought it was fool proof, but was apparently to much fool for it to handle.  Good news is I discovered that I don't have any need to use XP anymore.

---

### Post by halitech on 2008-03-06
as the saying goes, make something fool proof and someone will develop a better fool ;) 

been there, done that myself so don't feel bad

---

