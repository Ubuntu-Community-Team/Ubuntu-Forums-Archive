---
title: "logging on promblem"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by cingh on 2007-01-05
hi guys, well whenever i turn on the laptop (ubuntu 6.06) i cant make it load to log on, its fine until i get to mount files, it says Failed in red and then some sort of files are damaged and it said type CONTROL -D to check and reboot, i write CONTROL -D but nothing happens. so then i try to go on reboot and the same promblem happens, please help me this is serious. 

Cingh

---

### Post by taurus on 2007-01-05
What are you trying to mount?

---

### Post by macogw on 2007-01-05
Did you type the word "CONTROL" or press the Ctrl key?

Can you try booting it in recovery mode and typing:
fsck /dev/hda1 -y

replace /dev/hda1 with the partition of your root install.  If it's a SATA drive, that might be /dev/sda1

That'll check the file system and fix any errors it finds.

---

### Post by cingh on 2007-01-05
thank you guys 

ill try this soon 

cingh

---

