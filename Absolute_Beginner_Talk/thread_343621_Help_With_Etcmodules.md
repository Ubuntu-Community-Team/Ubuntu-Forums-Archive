---
title: "Help With Etc/modules"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by GILBERTO15 on 2007-01-21
i have an ibook g3, i enter these commands in the terminal modprobe snd-powermac and sudo modprobe snd-powermac and these enable me to use sound, but after restarting my computer i lose sound, on a post said to put these in etc/modules, so i enter sudo nano etc/modules and i am in but i dont know how to get out of here to save the thing i entered.

---

### Post by handaxe on 2007-01-21
When finished entering text in nano:

either cntrl+O to get a prompt for file name to save (it should be there with correct path), or:

cntrl+X to exit, which will prompt you to save the file.

HA

---

### Post by Shatrat on 2007-01-21
in nano
ctrl + o is save (output)
ctrl + x is exit
nano is great because you can still use it if you kill your graphical environment, but you might be more comfortable with gedit
try
gksudo gedit /etc/modules

---

