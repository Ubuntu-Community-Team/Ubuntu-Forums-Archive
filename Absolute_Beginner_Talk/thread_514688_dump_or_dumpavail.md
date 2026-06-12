---
title: "dump or dumpavail"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by desijays on 2007-08-01
what is the differrence between 

apt-cache dump 
apt-cache dumpavail

---

### Post by milosz.galazka on 2007-08-01
Hello,

From manual:
apt-cache dump
          dump shows a short listing of every package in the cache. It is
          primarily for debugging.

apt-cache dumpavail
          dumpavail prints out an available list to stdout. This is suitable
          for use with dpkg( 8 ) and is used by the dselect( 8 ) method.

---

