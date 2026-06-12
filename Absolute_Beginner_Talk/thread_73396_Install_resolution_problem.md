---
title: "Install resolution problem"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by chickennoodle soup on 2005-10-08
ok i went to install using default, and it loaded everyhting but after it said starting system log damien(sp?)  my monitor flases and says out of range 13.2kHz/25Hz  i tried the ctrl+alt+- thing and the screen=800x600 thing but nothing worked :-\  and thats all the advice i could get from my friends who use linux.  so any help please im clueless to thing :confused:

---

### Post by aysiu on 2005-10-08
Have you seen [this](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)?

---

### Post by chickennoodle soup on 2005-10-08
arnt those if u already are in the program? (im such a nub :-P)

like my hd is completly blank i havent even like installed it yet :-\

---

### Post by aysiu on 2005-10-09
There's some kind of boot option (instead of just hitting enter) where you can specific vga=791 or something like that. Do you get *any* kind of boot screen at all when you put the CD in?

---

### Post by chickennoodle soup on 2005-10-09
it gets the installer boot up screen where it has ubuntu graphic and says f1 for help andto install base system type server and enter or just to install press enter  but in f1 i cant seem to find any place to change the screen resolution

---

### Post by aysiu on 2005-10-09
Have you tried typing ```
linux vga=791
``` at the boot prompt? If that doesn't work, you can press F2, F3, F4, F5, etc. for more boot options.

---

### Post by chickennoodle soup on 2005-10-09
k its working now thx sir :)

---

