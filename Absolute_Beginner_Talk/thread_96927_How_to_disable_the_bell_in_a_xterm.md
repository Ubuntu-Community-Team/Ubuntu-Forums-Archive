---
title: "How to disable the bell in a xterm?"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by guyomarj on 2005-11-29
I need to launch an xterm, through the command line, and I want it to have neither the ringing bell, nor the visual bell (a.k.a. "The annoying flashing xterm").

I want a command line because I'm using Fluxbox.

Thx.

---

### Post by amohanty on 2005-11-30
xterm -vb

AM

---

### Post by guyomarj on 2005-11-30
[QUOTE=amohanty]xterm -vb[/QUOTE]
Thx, but it just switch from "Ringing Bell" to "Visual Bell", and I want none of them :(

---

### Post by amohanty on 2005-11-30
put the following in you .bashrc
xset -b
OR
set bell-style none

or put his in your .Xdefaults file:
xterm*visualBell: false

---

### Post by guyomarj on 2005-11-30
Thx. I'll try that as soon as I get back home.

---

