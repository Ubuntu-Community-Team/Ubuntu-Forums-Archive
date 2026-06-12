---
title: "Damn small linux desktop info tool for Ubuntu"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-08-31
on the desktop of DSL there is a cool utility that runs on the desktop on the rightside of the desktop and tell you some info about the machine it is running on.

this screenshot shows the tool

[http://damnsmalllinux.org/dsl-2.3jwm.jpg](http://damnsmalllinux.org/dsl-2.3jwm.jpg)

its on the right and the last of it says "host:box 192.168.1.101"

i would love to have that entire tool box running on Ubuntu.anyone know how to achieve this?

---

### Post by ddrichardson on 2007-08-31
Its called [torsmo]("http://torsmo.sourceforge.net/")

---

### Post by Sef on 2007-08-31
> Its called torsmo

Actually, it likely is [Conky]("http://conky.sourceforge.net/"), which is in the Universe repository.

---

### Post by bodhi.zazen on 2007-08-31
yes, Conky is in the repos, but it needs to be set up :

[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html)

---

### Post by ddrichardson on 2007-08-31
> **Sef said:**
> Actually, it likely is [Conky]("http://conky.sourceforge.net/"), which is in the Universe repository.

It is torsmo in DSL, however Sef is right in so far as Conky is a little easier to configure and much easier to install as its in the repository. Also torsmo can look odd on Xorg as it sometimes conflicts with the dektop wallpaper, creating a flickering effect - particularly with compiz

---

