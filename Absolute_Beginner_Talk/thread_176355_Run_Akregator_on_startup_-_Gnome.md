---
title: "Run Akregator on startup - Gnome"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by infoseeker on 2006-05-14
I would like to run Akregator on startup and minimised in the panel.

What would be the easiest way to do this?
I tried adding it into '.gnomerc' but it runs up as expected, not minimised.

KDE starts it up the way that I would like it to, but not in Gnome.

Anybody ?

---

### Post by fireduck on 2006-06-06
I just got Akregator to start minimised. I am using:
System -> Preferences -> Sessions
On the 'Startup Programs' tab I added the command:

/usr/bin/akregator --hide-mainwindow 

Seems to be working fine.

---

