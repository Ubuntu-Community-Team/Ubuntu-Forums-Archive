---
title: "Kernel config"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by Ubuntuud on 2006-02-13
What's a kernel config file? A log file says that it can't find it, does it mean my xorg.conf?

---

### Post by uopjohnson on 2006-02-13
The kernel is the core of any operating system.
When a new kernel is built all of the options that it uses are saved in a config-KERNELVERSION-ARCH file in your /boot directory.  It is possible that a program is looking for it in /usr/src/linux which is where it would probably be if you built your own kernel.  What program is leaving the log entry?  If it aint broke then don't worry about it.

---

### Post by Ubuntuud on 2006-02-13
Well, it doesn't work, it's a driver for my 3d accelerator. And would it help if I simply copied the file?

---

