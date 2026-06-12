---
title: "how to kill xwindows and keep it dead"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by natialos on 2007-08-09
How do I kill Xwindows and keep it dead? Ctrl+Alt+Bkspc restarts it, and whenever I try the kill command, that restarts it, too.

---

### Post by Saner on 2007-08-09
Ctrl + Alt + F1

---

### Post by natialos on 2007-08-09
That does not kill xwindows, it simply changes to a console screen.

---

### Post by splintercellguy on 2007-08-09
sduo /etc/init.d/gdm stop I think.

---

### Post by natialos on 2007-08-09
> **splintercellguy said:**
> sduo /etc/init.d/gdm stop I think.
Oh yeah! Except it's "sudo" and for me it's kdm, not gdm, because I have kde.

---

### Post by Rocket2DMn on 2007-08-09
If you want to live in the command line, you can open a terminal and run
```
init 3
```
This will keep you in runlevel 3 (multi-user command line interface only).
If you change your mind, you can get back to graphical mode (runlevel 5) with
```
init 5
```
These might require sudo, but I don't recall and am not in front of my computer to test them.


If you want it to be permanent, like even after you restart your computer:
```
sudo nano /etc/inittab
```
and change "id:5:initdefault:" to "id:3:initdefault:"

---

