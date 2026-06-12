---
title: "Synaotic: wanting to remove Ubuntu-destop"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by justleen on 2007-03-27
Hey All,

I wanted to remove Totem player through de Synaptic Packet Manager, so i marked it for uninstall (marking for complete removal did the same), en pressed aplly. 
In the review, synaptic showed the totem package as expected, but also Ubuntu-desktop...

Why would it wanna do that??

---

### Post by 1/0 on 2007-03-27
I got the same thing when removing gnome spreadsheet and abiword. I just hit OK and the desktop was fine so I guess its just a bug...

---

### Post by Kobalt on 2007-03-27
It's not a bug : ubuntu-desktop package is a meta package, it's a package that's actually empty but calls for a whole of packages, these being the ones needed to install a basic desktop. Since Totem comes installed by default it's depended on by ubuntu-desktop...
Removing ubuntu-desktop is just fine since you already have all those needed packages installed once you installed your system, and you can remove those you don't want anymore.

---

### Post by msak007 on 2007-03-27
As Kobalt said, it's just the meta-package that encompasses all the default installed apps. Removing one of those apps breaks the "package", but won't uninstall anything else (unless it depends on the app you're uninstalling and is no longer needed). It's safe, but there's one thing to remember: if you're doing this and plan to do a dist-upgrade to an updated release when it comes out (whether it be Feisty or any release afterward), you have to make sure to reinstall the ubuntu-desktop package so it grabs everything that's updated.

---

