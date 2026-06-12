---
title: "Menus in XGL &amp; Compiz"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-09-20
Hi, I was wondering where I could find the setting for the bouncing menus in XGL & Compiz, by this I mean when clicking on file, edit etc it bouncing open and wobbling about a bit, the effect doesn't work right for any of my KDE apps running in Gnome and slows using the menus down so really I just want to turn it off. I'm guessing its somewhere in csm but I don't know where, can anyone help?

Calv

---

### Post by MaXiMuS-D on 2006-09-20
I couldn't do it via CSM. I went into gconf-editor > apps > compiz > plugins > wobbly > screen 0 > options > window_types and removed menus and unknown types from the list.

If you're running compiz using the script described at ubuntuguide.org then just edit the script. It has a list of plugins to load as parameters to the compiz (?) command. Remove wobbly from this parameter list (but this will remove wobbly altogether).

---

### Post by calvinthomas on 2006-09-20
> **MaXiMuS-D said:**
> I couldn't do it via CSM. I went into gconf-editor > apps > compiz > plugins > wobbly > screen 0 > options > window_types and removed menus and unknown types from the list.

If you're running compiz using the script described at ubuntuguide.org then just edit the script. It has a list of plugins to load as parameters to the compiz (?) command. Remove wobbly from this parameter list (but this will remove wobbly altogether).

I follow your instruction up until window_types, that I don't have at all. I'm not sure exactly how i'm running it, i'll look into it though!

Calv

---

### Post by calvinthomas on 2006-09-20
I found it is csm, by going into csm, then wobbly windows, then changing map effect from shiver to none.

Calv

---

