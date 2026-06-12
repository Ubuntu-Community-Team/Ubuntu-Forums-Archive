---
title: "Launching software"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Sordelka on 2007-12-18
Let's say I want to launch some program from the terminal. What are the commands?

---

### Post by spiderbatdad on 2007-12-18
try typing the name of the program

---

### Post by mahiyar on 2007-12-18
If it is a programme with admin rights you want to open pu sudo in forn of the programme name like >> sudo gedit XYZ.

P.S: Graphical programmes are invoked with gksudo

---

### Post by aysiu on 2007-12-18
It's not always the name of the program, but it often is.

For example, to launch Firefox from the terminal, you'd type ```
firefox
``` To launch Add/Remove, however, you'd type ```
gksudo gnome-app-install
``` To launch F-Spot, you'd type ```
f-spot
``` but to launch Gnome configuration editor, you'd type ```
gconf-editor
``` Why don't you tell us what program you're trying to launch?

---

### Post by Sordelka on 2007-12-20
I am trying to launch a game to check what errors it will give me because when I actually do it graphically absolutely nothing happens. Like not even an error poping up.

---

### Post by hyper_ch on 2007-12-20
And the name of the binary doesn't fit with the program names you can still "edit" the applications menu and see what command/binary is run there.

---

### Post by philinux on 2007-12-20
> **Sordelka said:**
> I am trying to launch a game to check what errors it will give me because when I actually do it graphically absolutely nothing happens. Like not even an error poping up.

Are you going to tell us the name of the game or should we guess. :lolflag:

---

### Post by Sordelka on 2007-12-20
Sorry.

It is Fish Fillets.

I got an error after trying to sudo aptitude install fillets

When I launch fillets it says: 

main.cpp:117: ERROR Init; SDL='No available video device'

---

### Post by philinux on 2007-12-20
Well looking in synaptic it's called **fillets-ng**

so if I had installed it via synaptic and it did not put a menu item in for me then I would use terminal and type fillets-ng.

---

