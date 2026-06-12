---
title: "firestarter issue"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-06-06
i was having problems seeing my samba shares from my windows machine so i went to check my firestarter configuration. i wanted to make sure i wasn't blocking my windows machine. well, this is what i got when i tried to open firestarter

sudo firestarter -&
[1] 10578
shane@linuxmachine:~$ Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:10578): Gtk-WARNING **: cannot open display:

[1]+  Exit 1                  sudo firestarter -
shane@linuxmachine:~$ sudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:10585): Gtk-WARNING **: cannot open display:
shane@linuxmachine:~$ firestarter
shane@linuxmachine:~$ sudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:11100): Gtk-WARNING **: cannot open display:


any ideas? thanks!

---

### Post by yabbadabbadont on 2006-06-06
Try

gksu firestarter

instead.

---

### Post by shanepardue on 2006-06-06
gksu firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:11342): Gtk-WARNING **: cannot open display:

---

### Post by xXx 0wn3d xXx on 2006-06-06
I also had this problem. It can easily be fixed by reading [ this tutorial. ](http://ubuntuforums.org/showthread.php?t=187899)

---

### Post by shanepardue on 2006-06-06
oh wow that worked as well as cleared up my samba issue!! i didn't know all my problems were coming from that!!

so is this a bug or something? how did that happen?

p.s. thank you for the help!

---

