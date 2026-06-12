---
title: "Install issue on laptop 7.1 ver"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by SameerAcharya on 2008-01-08
Hi Iam trying to install Ubunto 7.1 AMD 64 version on acer 4520 laptop with 160 Gb HDD. The system boots from Live CD in low screen resolution mode. The installation was done with default partition setup and goes thru successfully.

When I restart the system hangs, when I try to do it in recovery mode it starts and then fails and takes me to the (initramfs) prompt.

No fstab file in /etc directory seen.

When I try to exit from the shell it shows error :

Check root=bootarg cat /proc/cmdline
or missing modules, devices : cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/<big uuid number> does not exist. Dropping to a shell.

I have tried re installing , redoing partitions and almost everything I could think of still no luck.

Please can anyone help me out. Or you can suggest which distro to work with.

---

### Post by Nano Geek on 2008-01-08
The CD might be corrupt. Try using the CD check at the boot-up screen when you put in the CD.

---

### Post by GepettoBR on 2008-01-08
If you end up reinstalling again, it would be a good idea to run the [GParted LiveCD](http://gparted-livecd.tuxfamily.org/) first and reformat your partitions prior to the install, to keep the old faulty installation from interfering with the new one. If you don't feel like downloading and burning the ~50MB ISO, GParted is included in the Ubuntu LiveCD as well, but it loads and runs much faster from its own LiveCD.

---

