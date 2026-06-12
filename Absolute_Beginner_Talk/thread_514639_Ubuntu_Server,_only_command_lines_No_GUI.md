---
title: "Ubuntu Server, only command lines? No GUI?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by texplorer on 2007-08-01
I want to be able to test my php webpage and MySQL  on the server. Which GUI should I get, and how do I install it please?

Thanks,

---

### Post by wolfen69 on 2007-08-01
after install:
```
sudo nano /etc/apt/sources.list
```
then remove any # symbols that come before any line starting with "deb"
ctrl-x, then Y, then enter.
```
sudo apt-get update
```
```
sudo apt-get install gnome-core xorg gdm
```
when finished, you will have a basic gnome desktop

---

### Post by Paul133 on 2007-08-01
"sudo aptitude update && sudo aptitude install ubuntu-desktop" is not enough?

Sorry for the quotes; I forgot the "console" tag.

---

### Post by wolfen69 on 2007-08-01
i believe installing ubuntu-desktop also installs the default packages too. this is a server, not a gaming machine. installing gnome-core gives basic gui functionality only.(firefox, terminal, and not much else)

---

### Post by texplorer on 2007-08-02
> **wolfen69 said:**
> after install:
```
sudo nano /etc/apt/sources.list
```
then remove any # symbols that come before any line starting with "deb"
ctrl-x, then Y, then enter.
```
sudo apt-get update
```
```
sudo apt-get install gnome-core xorg gdm
```
when finished, you will have a basic gnome desktop

em, how do I launch this GUI?
Thanks

---

### Post by Alterax on 2007-08-03
as a standard user, type in the terminal:

startx

(No, I'm not kidding.)
You can run this as root, but doing so is like driving with your feet.  Some things just shouldn't be done, in this case it's too easy to hose something in a gui with full admin privileges.

---

