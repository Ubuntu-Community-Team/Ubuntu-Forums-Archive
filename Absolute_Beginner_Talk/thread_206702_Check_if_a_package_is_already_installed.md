---
title: "Check if a package is already installed"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by anson on 2006-06-30
How could I check if a package is already installed, with apt-get or something else??

Anson

---

### Post by az on 2006-06-30
[QUOTE=anson]How could I check if a package is already installed, with apt-get or something else??

Anson[/QUOTE]
dpkg -l |grep (package)

or just use synaptic.

---

### Post by tomski on 2006-06-30
you could use synaptic which live's in:
 system->administration->synaptic package manager

or from command line you can type:
aptitude

for a comand line gui

or you can type:
dselect 

for another type of comand line gui package manager

or if you dont need/like gui's you can type:
apt-cache search nameofpackage
then just use:
apt-get install nameofpackage
to install it

---

