---
title: "Switching OS's"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Tiamats_Chosen on 2008-01-16
Is there any way to switch between  windows and linux with out restarting my computer?  or at least some kind of linux emulator i can use is windows that will let me see the linux partition?

---

### Post by jan quark on 2008-01-16
you can try to install linux in a virtual environment using software like VMWare

just being curious: why do you want to do this:)?

---

### Post by bodhi.zazen on 2008-01-16
Look at VMWare, virtualBox, qemu ....

You can access you windows partitions from Ubuntu.

---

### Post by lgambett on 2008-01-16
To access the Ubuntu ext3 filesystem while in windows you need a specific windows driver like this;
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by SunnyRabbiera on 2008-01-16
VMware is a good bet

---

### Post by quandary on 2008-01-16
> **Tiamats_Chosen said:**
> Is there any way to switch between  windows and linux with out restarting my computer?  or at least some kind of linux emulator i can use is windows that will let me see the linux partition?

Are you talking of running programs, or read/write access to the filesystem only?

If you only want to read/write data from your linux partition on windows, visit:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

The above link is for windows 2000/XP. There is a version for windows Vista on sourceforge.

---

