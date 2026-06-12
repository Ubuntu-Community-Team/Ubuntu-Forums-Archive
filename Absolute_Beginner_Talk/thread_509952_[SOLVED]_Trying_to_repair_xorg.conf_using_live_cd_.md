---
title: "[SOLVED] Trying to repair xorg.conf using live cd -- is it possible ?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-07-26
Guess

---

### Post by jerrynewt on 2007-07-26
Sorry for being such a dumb-*** tonight. Getting tIred I guess. I am trying to back up my xorg.conf file and need to know the entry for command line. Thanks in advance.

---

### Post by sloggerkhan on 2007-07-26
sudo to have root permission, cp to copy, so 
$sudo cp /etc/X11/xorg.conf /etc/X11/backup.xorg.conf
You could use the recovery console, or, if you boot the live cd, you will have to mount your disks from the command line:
$sudo mount -a 
or something.

---

### Post by jerrynewt on 2007-07-26
Thank you for the quick reply and have a nice night.

---

### Post by sloggerkhan on 2007-07-26
> **jerrynewt said:**
> Thank you for the quick reply and have a nice night.

you're welcome, glad it worked.

---

### Post by Dien on 2008-02-17
> **sloggerkhan said:**
> sudo to have root permission, cp to copy, so 
$sudo cp /etc/X11/xorg.conf /etc/X11/backup.xorg.conf
You could use the recovery console, or, if you boot the live cd, you will have to mount your disks from the command line:
$sudo mount -a 
or something.

I have type sudo cp /etc/X11/xorg.conf /etc/X11/backup.xorg.conf. It's said "Try 'cp --help' for more information". :confused:

---

