---
title: "Where is beagle?"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Linux Lover on 2006-12-18
Last night I have installed beagle ```
sudo aptitude install beagle
``` but now i am typing beagle in the terminal but it is not working and i am getting message that, ```
command not found
``` if i give the following command ```
sudo apt-cache search beagle
``` it returns ```
beagle-dev - library for accessing beagle (development files)
libbeagle0 - library for accessing beagle (development files)
beagle - indexing and search tool for your personal data
beagle-backend-evolution - evolution data backend for beagle
kerry - a KDE frontend for the Beagle desktop search daemon
kio-beagle - beagle kio-slave
python-beagle - python bindings for beagle
```

it is seemed that everything is installed, but why i am not able to run beagle by typing in the terminal? please let me know what mistake i am doing.

---

### Post by BarfBag on 2006-12-18
You're probably typing the wrong thing to launch it.  Give me a few minutes and I'll surf around for you.

Edit - try:

> beagled

---

### Post by 454redhawk on 2006-12-18
Places--->Search

---

### Post by Linux Lover on 2006-12-19
> **BarfBag said:**
> You're probably typing the wrong thing to launch it.  Give me a few minutes and I'll surf around for you.

Edit - try:

Tried as per your suggestion but it returns as follows :
```
linuxlover@linuxlover-desktop:~$ beagled
(/usr/lib/beagle/BeagleDaemon.exe:7307): Gdk-WARNING **: locale not supported by Xlib

(/usr/lib/beagle/BeagleDaemon.exe:7307): Gdk-WARNING **: cannot set locale modifiers


```
Now the screen stops here and the beagle program not opening.

---

### Post by Linux Lover on 2006-12-19
> **454redhawk said:**
> Places--->Search

Exactly. Got it. Thank you. But can you say me why it is not opening from the command prompt?

regards
linuxlover

---

### Post by sonny on 2006-12-19
> **Linux Lover said:**
> Tried as per your suggestion but it returns as follows :
```
linuxlover@linuxlover-desktop:~$ beagled
(/usr/lib/beagle/BeagleDaemon.exe:7307): Gdk-WARNING **: locale not supported by Xlib

(/usr/lib/beagle/BeagleDaemon.exe:7307): Gdk-WARNING **: cannot set locale modifiers


```Now the screen stops here and the beagle program not opening.
Well you obviously have some locale problems... try searching in synaptics for xlib locale and see what gives you (sorry I'm not in Ubuntu right now).

---

### Post by macogw on 2006-12-19
It's beagle-search I think.

---

### Post by 454redhawk on 2006-12-21
> **Linux Lover said:**
> Exactly. Got it. Thank you. But can you say me why it is not opening from the command prompt?

regards
linuxlover

If you want to search in the terminal


```
beagle-query filename
```

Or

If you want to bring up the GUI from the terminal

```
beagle-search
```

---

