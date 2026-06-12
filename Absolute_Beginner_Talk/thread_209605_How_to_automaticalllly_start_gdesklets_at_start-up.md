---
title: "How to automaticalllly start gdesklets at start-up?"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by mrvgarg on 2006-07-05
Hi

How can I automatically start gdesklets when I start my computer?

---

### Post by cowley on 2006-07-05
goto system>preferences>sessions

then click the startup tab

then add

then for the command type gdesklets

simon

---

### Post by ciscosurfer on 2006-07-05
I am having the same issue here.  Tried going to Sessions > Startup Programs and adding:
```
/usr/share/gdesklets/Displays/starterbar-desklet/starterbar.display
```to no avail.  Anyone got the skinny on this? #-o

---

### Post by ciscosurfer on 2006-07-05
[quote=cowley]goto system>preferences>sessions

then click the startup tab

then add

then for the command type gdesklets

simon[/quote] This only starts the gDesklets Shell.  We want to actually start one of the gDesklets are startup.

---

### Post by cowley on 2006-07-05
this will display any gdesklets you have placed on the desktop.  ie if you want the starter bar goto the configuration menu via the gdesklet icon in the notification area, and goto toolbars/launcher in the left pane, and double click the starter bar.  this will place the starter bar in the desktop. configure as you wish via right mouse click (move it, add/remove launchers).  when you log back in so long as you have gdesklets in your startup session the desklet will appear.

hope this made sense

simon

---

