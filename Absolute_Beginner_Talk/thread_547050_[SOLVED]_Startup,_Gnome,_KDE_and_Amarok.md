---
title: "[SOLVED] Startup, Gnome, KDE and Amarok"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by farueulogy on 2007-09-09
I use amarok on my gnome ubuntu system. As many of you will know this means amarok has to load a number of KDE libraries when it starts up.

I was wondering if there was a way of loading these libraries at start up so when I start amarok it starts nearly as quickly as a native application.

I wouldn't be reducing the load time but instead shifting it to be part of the start up. Shifting this would improve my user experience.

Any ideas on how?

---

### Post by shae on 2007-09-09
One possibility if you use a music player like I do (all the time) is to set Amarok to load in Gnome Session Manager.  Simply place the command to open Amarok in a new entry.  I am not sure of any other way to get the libraries to load.

---

### Post by farueulogy on 2007-09-09
> **shae said:**
> One possibility if you use a music player like I do (all the time) is to set Amarok to load in Gnome Session Manager.  Simply place the command to open Amarok in a new entry.  I am not sure of any other way to get the libraries to load.

"amarok %U" is the command for launching amarok and I think I'll try this for now see what the load time is like for everything.

**I was wondering what the %U meant at the end of the command - any info would be awesome.**

---

### Post by dpar on 2007-09-09
[This]("help.ubuntu.com/7.04/user-guide/C/launchers.html") will show you those commands.

---

### Post by farueulogy on 2008-03-28
Solution: I now use rhythmbox instead - fits in better with the gnome theme etc. and does everything I want.

---

