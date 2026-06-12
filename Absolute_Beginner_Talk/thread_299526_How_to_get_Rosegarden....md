---
title: "How to get Rosegarden..."
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by koryo88 on 2006-11-14
I'm trying to get Rosegarden for my Ubuntu install but it's not showing up in synaptic and neither is Audacity if I wanted to subsitute. If I try to download it manually I get that the dependency "kdelibs4c2a" is not satisfiable but it is, in fact, installed so it shouldn't be an issue.

---

### Post by 23meg on 2006-11-14
They're both in the Universe repository, which you should enable.

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html)

---

### Post by koryo88 on 2006-11-14
Forgive me for being so green...but now that I have it, I can't figure out how to run it. :-k

---

### Post by wpshooter on 2006-11-14
I believe that there is still a bug with the Rosegarden program which is related to the timing setting of the Linux kernel.  At least that is what I found the last several times I have attempted to use it.

---

### Post by koryo88 on 2006-11-14
I've installed one other thing besides rosegarden so far but the only way I've figured out to run them is through terminal. Is there any way to put like an icon on the desktop for it?

---

### Post by 23meg on 2006-11-14
It should be available in your *Applications* menu under *Sound & Video*. You can drag that icon to the desktop, or create a launcher there by right clicking the desktop, choosing "Create Launcher", and entering "rosegarden" in the "Command" field.

If it's not in the menu, try restarting the GNOME panel with ```
sudo killall gnome-panel
```

You can also hit Alt+F2 and type the name of the program you want to run.

---

### Post by koryo88 on 2006-11-14
It's not in any of my menus but creating a launcher worked. Where do they store it by default? 

I also installed conquest and I want to get rid of it but I have no idea where it put it. I also tried to install ogre, which I believe is for 3d images but I don't know where it is or what the command for it is.

---

### Post by CatKiller on 2006-11-14
If you installed a program through Synaptic, you can look at the Properties of the package in the list to see where it puts all the files.

---

### Post by 23meg on 2006-11-14
Application files typically get installed all over your system when you install with a package manager. The executables themselves will reside in /usr/bin, which is in your default path, which in turn means that you can run anything you've installed by just entering the executable name in a terminal, with Alt+F2, as a command for a launcher like you did, and elsewhere. The executable name is almost always the name of the app, but not necessarily so.

---

### Post by jott27 on 2006-12-25
> **koryo88 said:**
> I've installed one other thing besides rosegarden so far but the only way I've figured out to run them is through terminal. Is there any way to put like an icon on the desktop for it?

Right click anywhere on the screen, Select 'Create New' then 'Link to application'
Type 'RoseGarden' and in the Application tap under commands type rosegarden.
If you want to be fancy you can also change the icon.
Good luck.

---

