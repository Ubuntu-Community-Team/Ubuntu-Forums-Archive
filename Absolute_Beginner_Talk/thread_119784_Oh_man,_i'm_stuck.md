---
title: "Oh man, i'm stuck"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by Cool Calm Chris on 2006-01-20
So I installed 5.10 on my old compaq armada m700 last night...went well, logged in, then tried to call up the GUI with apt/get install server/xorg...and no luck, it just switches me back to the command line after i choose color default settings..and, to compound things, the CD drive has stopped working! so now i REALLY need to get to the GUI but i'm stuck....hm..:confused:

---

### Post by Kapre on 2006-01-20
[QUOTE=Cool Calm Chris]So I installed 5.10 on my old compaq armada m700 last night...went well, logged in, then tried to call up the GUI with apt/get install server/xorg...and no luck, it just switches me back to the command line after i choose color default settings..[/quote]

Chris - This seems like a server type install. But if it is not, try typing startx. If this still doesn't work, try installing the usual (GNOME).


> and, to compound things, the CD drive has stopped working! so now i REALLY need to get to the GUI but i'm stuck....hm..:confused:

Reboot and if you have the LiveCD, pop it in.

K

---

### Post by jon_z on 2006-01-20
if you have had expierence with either use them, if not go with GNOME there seems to be much more support on the forums for that.
To install GNOME do the following
```
sudo apt-get install ubuntu-desktop

```To install KDE do the following
```
sudo apt-get install kubuntu-desktop
```
it will prompt you for your password, type it in and hit enter (you wont see anything be entered)  it will ask you about taking up disk space, press 'y' and enter and you should be on your way, once it is done, restart your computer and it should boot to gnome.

---

### Post by az on 2006-01-20
What packages did you install to get xorg?

You would need to install the meta package mentioned above or
x-window-system-core

You also need a window manager....

A small neat system can be install by enableing the universe repository (uncomment it in /etc/apt/sources.list), updating and installing

sudo apt-get install x-window-system-core gdm xterm menu icewm mozilla-firefox

---

### Post by Cool Calm Chris on 2006-01-20
Thanks for the advice..I tried everyone's suggestions, to no avail. Apparently, xwindows is already installed, it just won't come up. And I tried the Live CD trick, and the cd drive spools four times for three seconds, then just shuts off. It does this at startup and whenever a new cd is inserted.

Beats me...maybe it has some thing to do with the machine, and not ubuntu.

However, when I tried to install certain packages, the screen would say something like, "located but it will not be installed" (I'm about to leave and the other comp is shut off).

Maybe the CD I burned was bad?

---

