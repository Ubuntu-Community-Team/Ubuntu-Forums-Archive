---
title: "Persistent Ubuntu"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by kwjaxon on 2007-12-20
Started this by screwing up my dual boot.  Can only boot into Ubuntu.  Have tried numerous times to get rid of it so as to redo Windows.  I think I have formatted the HD about 10 or 12 times.  Ubuntu will still boot and am unable to insall new Windows to get back to my dual boot.  There are may things that I still use Windows for.  Many suggestions for cure but none work.  Anyone out there want to give it a try.  Appreciate any help.

---

### Post by saj0577 on 2007-12-20
Just put the windows disc in and install over the top is probably the easiest option then install linux again if your more comfortable with windows if you wish and you have a second pc i could talk you through it and give you live help.

Saj

---

### Post by ajgreeny on 2007-12-20
If you still have the windows partition and files intact, you can probably repair the windows MBR using fixmbr in the windows XP CD recovery console.  Once you have done that you can reinstall grub easily using the ubuntu liveCD.

---

### Post by Shazaam on 2007-12-20
Before you try anything open terminal and type this in so we can get a better idea what's on the drive(s)...
```
sudo fdisk -l
```
(small L)
This code will print out your disk info in terminal. Please post the output here.

---

