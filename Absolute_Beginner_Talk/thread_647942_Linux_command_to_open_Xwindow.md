---
title: "Linux command to open Xwindow"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by mannyk on 2007-12-22
Hi,
      I just installed the server version of ubuntu linux OS. 
Once started the system , it takes me to command line mode. 
Does anyone knows the linux command to open XWindow or GUI window? Please let me know.
                                                                   Thanks in Advance.

---

### Post by Victormd on 2007-12-22
If I'm not mistaken, type startx from the terminal...

---

### Post by kool_kat_os on 2007-12-22
I need the same help

---

### Post by Sef on 2007-12-22
> If I'm not mistaken, type startx from the terminal...

That is correct.

> I just installed the server version of ubuntu linux OS.
Once started the system , it takes me to command line mode.
Does anyone knows the linux command to open XWindow or GUI window? Please let me know.

The server version does not come with a GUI window.   

To install one type the following commands:

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

---

### Post by kerry_s on 2007-12-22
there is no gui for the server. you can install 1.
example:
sudo apt-get install xorg gdm xubuntu-desktop
reboot

gnome= ubuntu-desktop
kde= sudo apt-get install xorg kdm kubuntu-desktop

you can also just go with a window manager instead of a whole desktop system.

---

