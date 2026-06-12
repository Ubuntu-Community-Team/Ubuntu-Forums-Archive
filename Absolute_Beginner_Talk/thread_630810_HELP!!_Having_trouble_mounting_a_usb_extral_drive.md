---
title: "HELP!! Having trouble mounting a usb extral drive"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by trumants on 2007-12-03
[FONT="Arial"]I am having trouble mounting a 250 GB USB SimpleDrive.  It won't mount automatically, even when I tried a forced mount.  I got the following results.  I am really new to Linux and would really like to be able to use it, but this has me stumped:confused:
[/FONT]

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS
truman@truman-Ubuntu:~$ sudo mount -t ntfs-3g /dev/sdc1 /media/SimpleDrive -o force
[sudo] password for truman:
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/SimpleDrive: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdc1 (SimpleDrive)

---

### Post by Sarteck on 2007-12-03
When you plug it in, can you post the output of ```
dmesg | tail -n 100
``` ?

---

### Post by trumants on 2007-12-03
I don't know how it happened, but this time when I went into Places/Computer/SimpleDrive I was able to open it.  It was a miracle

---

### Post by Sarteck on 2007-12-03
The Self-Healing Power of Ubuntu!  It's a miracle!  XD

---

