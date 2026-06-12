---
title: "xorg.conf permission"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-10-29
how can i get permission to write in the xorg.conf file and basically all files on the Filesystem drive?...and can someone give me the command to open a file in Terminal, i mean if i want to view xorg in terminal what do i type? thanks

---

### Post by meng on 2006-10-29
sudo nano -w /etc/X11/xorg.conf

Actually even better is

sudo nano -Bw /etc/X11/xorg.conf
(which automatically creates a backup xorg.conf~ just in case you screw up)

If you just want to view but not edit, you can
cat /etc/X11/xorg.conf
and you don't need superuser privileges for that.

---

### Post by whatintheworldisthat on 2006-10-29
You can also of course replace "nano -Bw" with your favorite command line editor. (vi(m), emacs, etc.)

---

