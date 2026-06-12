---
title: "Rename grub entry"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by dropscience on 2008-04-05
Hi, i just want to know whether or not i can rename the grub options for Ubuntu at startup and if i can do it without breaking it? I want to rename the grub entries at startup. I've read in a few other threads and apparently i need to go into /boot/grub/menu.lst to do this, but isn't there some kind of software or graphical option too? 

Can somebody explain a little bit how to do this, i just like having a neat grub screen

Excuse my beginner question

---

### Post by LaRoza on 2008-04-05
Sure, run this command (or press Alt + F2)

```

gksudo gedit /boot/grub/menu.lst

```

You should make a backup of the original.

Lines starting with a # are comments and are ignored by the system.

You can change the title of anything, or comment out entries you don't want to be visible. The entries are at the bottom of the file.

---

### Post by dropscience on 2008-04-05
Ok great thanks! I will try that as soon as possible

---

