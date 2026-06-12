---
title: "Where are the Program Files?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by venik212 on 2007-01-23
I have installed several applications (for example, Rlplot) using Synaptic, but I need to know where they are.  I would like to start them with a gui (Gnome), rather than from the terminal.  When I search for them, typically Nautilus fails to find them.  Where are applications usually stored?  They are not listed under and of the Application submenus.

---

### Post by taurus on 2007-01-23
Usually in /usr/bin.  You can find out where it is from a terminal with

```
whereis **program_name**
```

---

### Post by hyper_ch on 2007-01-23
You could edit the Appz Menu in your gui and just enter the "programs' names" as new entry...

---

### Post by Phesto on 2007-01-23
This picture might help you understand the linux file structure. Hope it helps somewhat.

---

### Post by venik212 on 2007-01-23
Thanks-- that thumbnail was useful.  However, the question I am asking is really simple:
To run most programs, there is ONE file (script, binary, or link) that needs to be clicked to start the program.  Isn't there a single place where user installed programs are stored?  Intuitively I would imagine it to be in /usr/bin.  Is that where they hide?
In order to add anything to the Application menus I need to know -- at least-- the name of the script or binary associated with the program.
In Windows, after installation of a program, you usually see an icon on the desktop or in the Quick Launch bar.  It would have been a nice hand holding touch to have something like that in Linux.

---

### Post by ComplexNumber on 2007-01-23
> **venik212 said:**
> Thanks-- that thumbnail was useful.  However, the question I am asking is really simple:
To run most programs, there is ONE file (script, binary, or link) that needs to be clicked to start the program.  Isn't there a single place where user installed programs are stored?  Intuitively I would imagine it to be in /usr/bin.  Is that where they hide?
In order to add anything to the Application menus I need to know -- at least-- the name of the script or binary associated with the program.
In Windows, after installation of a program, you usually see an icon on the desktop or in the Quick Launch bar.  It would have been a nice hand holding touch to have something like that in Linux.
about 99.999999% of user installed applications are either installed in /usr/bin or /usr/local/bin or /usr/games. essential programs are stored in places such /bin, /usr/sbin, /sbin...but you don't need to bother looking in there.

---

### Post by 23meg on 2007-01-23
To figure out where files from a certain package are installed, right click the package in Synaptic, click "Properties" and go to the "Installed Files" tab.> 
In order to add anything to the Application menus I need to know -- at least-- the name of the script or binary associated with the program.
In Windows, after installation of a program, you usually see an icon on the desktop or in the Quick Launch bar. It would have been a nice hand holding touch to have something like that in Linux.Most apps already install their own menu entries. With those who don't, the executable is almost always in your default path, so all you need to know to create a launcher is the executable name, which is almost always the same as the package name, though not necessarily.

---

