---
title: "Personalized menu bar issues"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Diablos_Raven on 2007-05-24
My friend showed me this site about making your own personalized menu bar panel. [http://www.natewelch.com/index.php?name=News&file=article&sid=41](http://www.natewelch.com/index.php?name=News&file=article&sid=41)
In step 4 they say open gconf-editor and got to apps --> panel --> objects. Under apps --> panel I have default_setup, general, and global, but no objects. I'm curious on why that is. I have managed to do it before when i first installed feisty and then i was having issues with my system crashing and now i cant manage to do it again. HELP!

---

### Post by dstew on 2007-05-24
You might have to update the gnome menu package. You can see the package parts in Synaptic. They are gnome-menus, gnome-panel, and gnome-panel-data.

---

### Post by Diablos_Raven on 2007-05-24
Gnome-panel and gnome-menus were already installed but I couldn't find gnome-panel-data. I did however find some lib files and a couple of other things that were relative to the menu panels. I installed gnome-main-menu, libc6-dev, libglib2.0-dev, libgnome-menu-dev, linux-libc-dev and unfortunately it didnt change anything. I would like to give you screen shots but I'm not sure if I can or how to do so.

---

### Post by dstew on 2007-05-24
[Here]("http://packages.ubuntu.com/feisty/gnome/gnome-panel-data") is a link to the gnome-panel-data package for Feisty. Download it, and right-click to install.

---

### Post by Diablos_Raven on 2007-05-25
I have that installed, should I remove and reinstall via the package or is there a better way to do this. This is a little more advanced than I'm use to. I marked the gnome-panel for removal and it said it would remove gnome-desktop, alacarte, and a couple of other things. Wouldnt that hurt my system if I removed gnome-desktop. I tried to install straight from the package I got from the link you gave me and it said newest version installed.

---

### Post by dstew on 2007-05-25
If it said it is installed, then it is installed. I don't have any other ideas at present. Anybody else out there that can help us?

---

### Post by Diablos_Raven on 2007-05-25
Well I don't know what happened but it seemed to fix itself.  After reading the earlier post I threatened to remove gnome-panel-data just to find out what the dependencies were and then I logged into my wifes account to make her panel and it was there then I logged back into my account and it was there as well. So I don't know what happened and I probably never will bust thanks to all for the info.

---

