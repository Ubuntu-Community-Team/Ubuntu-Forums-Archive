---
title: "windows manager fix?"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by spiderbatdad on 2007-09-20
Running Fiesty now.
I seem to have lost my windows manager. I was running Beryl and Kiba-dock for a while, then Beryl stopped working, and Kiba would not work properly as a result. Later during a maintenance restart I received a warning that /etc/fstab was missing a new line.
Anyway, I have no windows manager at all not after removing Beryl and Emerald. Does anyone know how to reactivate gnome or metacity?

---

### Post by qamelian on 2007-09-20
Press Alt-F2 to get the "Run Application" box. On the command line, type: ```
metacity --replace
```.

This will set metacity as your window manager.

---

### Post by spiderbatdad on 2007-09-20
Thanks. Had been trying to run application, but alt-f2 wouldn't come up. I ended up reinstalling beryl and emerald and was then able to select a package manager and quit Beryl. Also I believe the theme was set in Emerald to one not compatible with Beryl or Gnome.

---

