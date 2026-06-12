---
title: "Program install not working"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by jbraum on 2005-10-13
I've just loaded kbuntu and would like load a program in but get the following.

admin@Lily:~$ sudo apt-get install frozen bubbles
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package frozen
admin@Lily:~$

Same thing we I try other installs.  I know I'm missing something:???:

---

### Post by mcduck on 2005-10-13
the packages you need are called frozen-bubble and frozen-bubble-data, so do 'sudo apt-get install frozen-bubble frozen-bubble-data'.

When you aren't sure what's the exact name for program you want, you can use search in synaptic. (kynaptic in KDE? I'm using gnome)

---

