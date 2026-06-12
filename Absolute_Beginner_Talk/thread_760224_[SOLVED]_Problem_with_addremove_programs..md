---
title: "[SOLVED] Problem with add/remove programs."
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by enazguy on 2008-04-19
Add/Remove programs will  not let me enable things for install. It says it needs to reload the list of programs i have installed.

---

### Post by frup on 2008-04-19
try opening terminal and typing sudo apt-get update. See  if that fixes the problem

---

### Post by indiecast on 2008-04-20
are you connected to the internet? cause im pretty sure you have to be connected to the internet

---

### Post by Pasty-Flawss on 2008-04-20
You got 2 options.

1) go to software sources (system > administration > software sources)
and check all boxes apart from source code then click on download from and click other.
then go chose best server then wait for it to do its thing then chose the one it has selected then it should work.

2)go to [http://www.packages.ubuntu.org](http://www.packages.ubuntu.org) and download from there

---

### Post by Saint Angeles on 2008-04-20
the add/remove thing doesn't seem to be as function as synaptic (for me at least)

check out synaptic package manager (system->administration) and hit "reload" and "mark all upgrades".

or in a terminal:

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by enazguy on 2008-04-20
the server thing worked
thanks

---

