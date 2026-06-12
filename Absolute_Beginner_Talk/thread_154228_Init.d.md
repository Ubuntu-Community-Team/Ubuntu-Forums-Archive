---
title: "Init.d"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by Compact on 2006-04-02
If I wanna run a program every time the system starts, I have to put a script in this folder to initialize the program like exec and the path of the program?

---

### Post by dcstar on 2006-04-02
[QUOTE=Compact]If I wanna run a program every time the system starts, I have to put a script in this folder to initialize the program like exec and the path of the program?[/QUOTE]
Yes, have a look at the existing scripts in /etc/init.d for exactly how you should structure your script.

The "skeleton" script is a template you should copy and modify for your own use.

Once that is done, you then have to link the script to the appropriate /etc/rc?.d directory so it runs when it is supposed to. Install the sysv-rc-conf package to manage this for you.

---

