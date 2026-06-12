---
title: "Where are the apps ??"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by gettinoriginal on 2007-03-17
My sig says dont wade, well, I am feeling like I should get a life jacket  LOL.  I have installed some packages from Automatix and Synaptic, and now I can't find some of them.  Where does a person go to find things when they dont show up under Applications ??  I know this must have been asked before, but I cannot find it in my search.  Thanks for the help

---

### Post by taurus on 2007-03-17
Depends on what package you install; most of them are in /usr/bin.  Just open a terminal and type in the name of the program to run it.

Applications -> Accessories -> Terminal
```
program_name
```

---

### Post by gettinoriginal on 2007-03-17
with all the wierd names of programs, how are am I to know what to type, I only picked them by description and function, not by name !!!  :(

---

### Post by bapoumba on 2007-03-17
Some packages will put an entry in the menu, but you have first to:
```
killall gnome-panel
```
to refresh the menu entries (when applicable).

---

