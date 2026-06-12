---
title: "desktop icons - how"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by thorby on 2007-10-31
Boy this has to be a beginner question. I've installed 7.10 and the gnome desktop is absolutely empty. Nice to finally have a clean desk, but I'd like to have icons on the desktop for the computer and my home folder. Yeah, I can see I get to them directly from the Places menu! But I'd like an icon.

Can't figure out how to do it. When I try to drag my home directory to the desktop, I get a message about trying to put something inside itself, "desktop" being a file inside my home directory. Anyway... comfy objects? How?

---

### Post by Carbon Tiger on 2007-10-31
Simple really :)

Go onto your desktop and click on places then go down to computer and hold down the mouse button and drag and drop it on your desktop that'll make a short cut. You can also drag and drop programs this way either to the desktop or onto the panels as well.

Home folder you need to make a launcher icon on your desktop to do that.

Right click on desktop create launcher select location as type, choose an icon, name the launcher and the location is file:///home/ that should do it, feel free to correct me if I'm wrong.

---

### Post by DSn0wMan on 2007-10-31
You can just drag application shortcuts from the munu to the desktop, but it's not a good idea with folders.

Your home folder is /home/username
Your Desktop is /home/username/Desktop

So it makes sense that you can't put your home directory inside the desktop directory.

For folders you want to use symbolic links (shortcuts), but its not a good idea to link to a directory directly above the directory you are in. The best thing for the home directory is to drag the icon from places onto your panel.

---

### Post by jayson.rowe on 2007-10-31
The correct way (and will produce better results) - pull up a terminal and run gconf-editor

once in there navigate to apps>nautilus>desktop and check the boxes for Home and Computer (and documents and trash if you want them)....

Changes are applied instantly.

---

### Post by thorby on 2007-10-31
gconf-editor, perfect, thank you!

---

### Post by Eddie002Fast on 2007-10-31
Nautilus is the best way that i have found and i use that method myself!!!  :-D

---

### Post by kremeru on 2007-11-06
Hello.

I´m using Ubuntu 7.10
In 7.4 I had disabeld the desktop icons in gconf-editor with apps-nautilus-preferences-show desktop because I tried to use fluxbox instead of metacity.
now I´d like to have Icons again on the Desktop (not using fluxbox anymore) but it doesn´t work  to enable that option again.
Can someone help?

---

### Post by MikeTheC on 2007-11-09
I'm also having this problem in both Gnome and KDE on my recently-installed 7.10 PPC.

I've gone into gconf-editor and it just ignores my checking of the boxes.

Thoughts?

---

### Post by kremeru on 2007-11-10
hello
now it suddenly works...I don´t really know why maybe it needs to be restarted a few times...?

---

