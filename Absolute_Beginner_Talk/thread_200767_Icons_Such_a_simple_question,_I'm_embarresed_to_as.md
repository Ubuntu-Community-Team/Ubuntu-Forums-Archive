---
title: "Icons: Such a simple question, I'm embarresed to ask..."
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by Narpas on 2006-06-20
How do I add icons to the /usr/share/pixmaps/ directory, and have them come up in the icon menu? I've used Ubuntu for about three months now, but that's one thing I've just never found a howto for.

---

### Post by th3james on 2006-06-20
you should just been able to add them in their as the root user
(if you want a root file manager: gksudo nautilus)

---

### Post by user1397 on 2006-06-20
[quote=Narpas]How do I add icons to the /usr/share/pixmaps/ directory, and have them come up in the icon menu? I've used Ubuntu for about three months now, but that's one thing I've just never found a howto for.[/quote]well there's a graphical way, and a command-line way, but i'll explain both.

Command-line way: Open a terminal (applications > accessories > terminal), put your icon on the desktop, and paste these one line at a time: 
```
cd Desktop
sudo mv iconname /usr/share/pixmaps
``` replacing filename with the actual icon's name.

Graphical way: Press ALT+F2, and type **gksudo nautilus** and then you'll be in nautilus, the file browser, but with root permissions, so you can do anything.  Then just drag your icon file into /usr/share/pixmaps, and close nautilus.

---

### Post by Narpas on 2006-06-20
Huh. It didn't work before. Oh, well. Works now! Thanks!

---

