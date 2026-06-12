---
title: "KDE applications in GNOME / XFCE"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-04-25
I want to run KDE applications in Gnome / XFCE. There must be some way to do it without
installing KDE desktop and running KDE.
Will KDE-core help ?

---

### Post by aberry5555 on 2007-04-25
its very easy to do, go to accessories and open up synaptic, then find and install the kde libraries (the description should explain which one is the right file). Once you've done this, install the kde programs you want et voila, they'll work :)

one thing you might want to consider, though, would be to add the kde libraries at startup under

/etc/rc.local

as I find, if I don't do that, then it takes 10-15 seconds to load up the first kde program you run.

---

### Post by meborc on 2007-04-25
when you trie to install a kde app under gnome or xfce, it automatically installs all the libraries needed... so just go to synaptic and try to install amarok (an excellent music player) for example... after install run it :) no problems

---

