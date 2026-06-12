---
title: "removing programs that came with ubuntu"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2007-03-27
ok i want to remove some of the programs that came with ubuntu and when i use synaptic to do it a message comes up saying it have to remove ubuntu desktop also. thanks for the help people!
ps and if anyone knows how to put the trash on the desktop that would help too thx

---

### Post by zvacet on 2007-03-27
Ubuntu desktop is meta-package and you can remove it.I don´t know why do you want to remove packages wich comes with Ubuntu but you probably have your reasons.

---

### Post by antgul3382 on 2007-03-29
i want to remove things like ekiga, bittorrent, some games and fspot......so if i remove them witrh synaptic and it says its removing ubuntu-desktop its not gonna mess it up???

---

### Post by chris062689 on 2007-03-29
Right.
This is the same problem I had when I first had Ubuntu.
the ubuntu-desktop is like... a collection of programs (GNOME desktop, and the programs that come preinstalled), but each one is seperatly installed, removing one program ONLY removes that one program.

---

### Post by Panzor on 2007-03-29
Well, you can always pick and choose which programs you'd like to get ride of.

sudo aptitude remove <insert program name here>

---

### Post by sagara on 2007-03-31
I'll try to explain this:

There is **no true harm** in removing the ubuntu-desktop package.  However before you go ahead and do that please be aware of the purpuse of this package.

The ubuntu-desktop package is pretty much a file that tells ubuntu what are the default applications it came with (pre-installed apps like evolution and firefox among others).  Ubuntu uses this list to look for automatic updates for these programs.  **If you delete this file**, nothing bad will happen but then ubuntu will stop automatically notifying you of updates for any of these programs.

The choice is yours really...  the pre-installed programs don't take much space so it won't hurt to just keep them.


To put the trash in your desktop just:
1. Hit **alt-F2** and run 'gconf-editor'
2. Browse to apps/nautilus/desktop
3. Enable 'trash_icon_visible'

---

