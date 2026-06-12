---
title: "Permission to copy files"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by dphirschler on 2007-07-23
I know this should be the simplest question.  I want to copy my Mame roms from one PC (Windows XP) to another via the network.  I've located the files on the Windows machine, and when I attempted to drag them to /usr/share/games/xmame/roms/ I got the message that I did not have the permission to copy to that folder.  So how do I give myself that permission?


Darryl

---

### Post by pyros on 2007-07-23
hit alt+f2 to get the run application window, then type 
```

gksudo nautilus /usr/share/games/xmame/roms/

```
gksudo will ask you for your password and then should open a file manager with permission to write to that directory.

---

### Post by asmoore82 on 2007-07-23
I would put the ROMS somewhere you already have permission to put them...
like <your home>/.xmame/roms

---

