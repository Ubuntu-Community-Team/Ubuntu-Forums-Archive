---
title: "copy files to filesystem"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by smudje on 2006-09-10
Hi, I want to copy some splash images to the grub directory on filesystm, hoverever it obviously wont let. How do I do this ? Any help apreciated.

---

### Post by elpuerco on 2006-09-10
run sudo cp <source file name> <destination file name> from a terminal

---

### Post by Najand on 2006-09-10
> **smudje said:**
> Hi, I want to copy some splash images to the grub directory on filesystm, hoverever it obviously wont let. How do I do this ? Any help apreciated.

Use sudo. i.e. use:
```
sudo cp YOURFILE /boot/grub/DESTINATION_DIRECTORY
```
(change YOURFILE and DESTINATION_DIRECTORY with the suitable names.)

---

### Post by smudje on 2006-09-10
i must be doing somjething wrong   but can't get it to work, I'll keep trying.

---

### Post by taurus on 2006-09-10
> **smudje said:**
> i must be doing somjething wrong   but can't get it to work, I'll keep trying.
Exactly what did you type?  If you show what you did, then somebody will tell you what's wrong with it...

---

