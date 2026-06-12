---
title: "Gnome panel urgent help!"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Cubedude04 on 2007-09-20
I accidentally deleted gnome panels (i mean the whole shell or program not just the actual panel) 

i went into the command line (alt f2) and wrote

sudo apt-get install gnome-panel and it says

The following packages have unmet dependencies 
gnome-panel : Depends: gnome-panel-data (= 1:2.18.1-0ubuntu3.1) but 1:2.18.1-0ubuntu3.2 is to be installed

E:Broken packages

What should i do?

I tried 

Sudo apt-get install gnome-panel-data and it says it's at the latest version

---

### Post by alienexplorers on 2007-09-20
Do a:
> sudo aptitude update
sudo aptitude upgrade
sudo aptitude install gnome-panel-data
sudo aptitude install gnome-panel

---

