---
title: "Help...Pygame dependencies?"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-12-29
I am trying to get a python game to work on my pc and it says this:

[user@localhost pygame-1.7.1release]# ./setup.py
Using UNIX configuration...

No Arguments Given, Perform Default Install? [Y/n]y

WARNING, No "Setup" File Exists, Running "config.py"

Hunting dependencies...
sh: sdl-config: command not found
WARNING: "sdl-config" failed!
sh: smpeg-config: command not found
WARNING: "smpeg-config" failed!
Unable to run "sdl-config". Please make sure a development version of SDL is installed.
[root@localhost pygame-1.7.1release]# apt-get install sdl-config
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package sdl-config

I'm not familiar with python stuff whatsoever and am probably not prepared for it either.  I tried [www.libsdl.org](www.libsdl.org), synaptic and apt-get. I can't seem to get this seemingly simply thing to work.. Anyone know how to get my program to work here?

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Be the change you want to see in others
                                          -Ghandi

---

### Post by Apple 101 on 2006-12-29
> Couldn't find package sdl-config

Open Synaptic, and install the sdl-config package and the sdl-dev package, and their dependencies, if any.

---

