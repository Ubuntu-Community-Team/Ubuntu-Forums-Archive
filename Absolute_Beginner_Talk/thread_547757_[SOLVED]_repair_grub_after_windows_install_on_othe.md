---
title: "[SOLVED] repair grub after windows install on other partition"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by LegeDoos on 2007-09-10
Hi there,

I have 3 partitions:
-winxp
-win2003 server
-unbuntu

All wordked fine until I reinstalled win2003 server: GRUB doesn't load anymore.

How can I recover GRUB (to the mbr) using the Live CD?

Regards,

Rob

---

### Post by alienexplorers on 2007-09-10
Follow the link in my siganture line.

---

### Post by prince_niceguy on 2007-09-10
check this out...

[http://ubuntuforums.org/archive/index.php/t-24113.html]("http://ubuntuforums.org/archive/index.php/t-24113.html")

---

### Post by Duck2006 on 2007-09-10
From the terminal on the live cd

sudo grub

at the grub promp

find /boot/stage1

it will come back with something like

(hd0,2)   use what it comes back with

root (hd0,2)

setup (hd0)

quit

Then reboot and grub sould be back for you

---

### Post by LegeDoos on 2007-09-10
Thnx!!

---

