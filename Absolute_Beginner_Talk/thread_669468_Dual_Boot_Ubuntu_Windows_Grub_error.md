---
title: "Dual Boot Ubuntu Windows Grub error"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by TGCIL on 2008-01-16
Alright so I have a Laptop that has Windows XP Tablet Edition I recently Added Ubuntu and set up a dual boot. When I was setting up Ubuntu I found that after loading windows the grub file would be damaged, so I booted from the CD and did the following steps

sudo grub
find  /boot/grub/stage1
[Output would be (hd0,1)]
root (hd0,1)
setup (hd0)
quit

This would seem to fix the grub file. It seemed to work for 3-4 weeks Then recently almost whenever I boot windows after shutting down the grub file would be damaged.

One time I fixed the grub as above opened windows, did nothing shut it down and when I loaded it again the file was damaged

what can I do, I love linux but I have programs on windows I need to be able to use, it's a pain to have to constantly boot from a cd and repair a grub file all the time,

Thanks in advance

---

### Post by eolson on 2008-01-16
Download a copy of

    supergrub

and see if that will fix it.

I forget the url,  but a quick google should get it.

---

### Post by dstew on 2008-01-16
Maybe Windows is running a disk check program that is "repairing" your boot record for you.

---

