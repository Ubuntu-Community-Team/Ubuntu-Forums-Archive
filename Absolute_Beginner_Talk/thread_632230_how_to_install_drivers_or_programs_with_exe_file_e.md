---
title: "how to install drivers or programs with *exe file extention?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by csdeathtrap on 2007-12-05
specifically my motherboard driver & videocard driver nvidia 7300gt...
thanks

---

### Post by Dr Small on 2007-12-05
> **csdeathtrap said:**
> specifically my motherboard driver & videocard driver nvidia 7300gt...
thanks
Greetings and welcome to Ubuntu Forums,
Please read this article:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

Dr Small

---

### Post by Hospadar on 2007-12-05
you won't use those binaries (the .exe files), they are for windows and won't work/do anything under linux.  the driver you need from your video card can be got at through the restricted driver manager System->Administration->Restricted Driver Manager

you shouldn't really need any other drivers, unless you have some funny hardware or specific problems.  if that's the case, holler and we'll try to find what you need.

In general, your windows programs won't work in ubuntu, but there are many great native-to-linux alternatives for all but a few of the biggest professional software packages (and games of course!)

If you want to try running windows programs under linux, there are some things that may allow you to do that, virtual boxes, wine.  but these don't always work, and will do nothing for drivers and system software like that, they are generally only useful for user applications.  The reason for this being some very low-level mumbo jumbo, but basically, windows drivers provide the correct interface for windows to use your hardware, and so even if you managed to somehow install that stuff, linux wouldn't know what to do with it.

Hope that helps clear up some confusion!
happy linuxing

---

