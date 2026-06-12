---
title: "Can't modify my Xubuntu menu!"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by itchanddino on 2006-08-30
I click Menu Editor under System in Xubuntu, but none of my installed applications are on the list.  It seems that they are ALL displayed as one simple line that looks like 
---include---          system
All of the other entries, such as Run Program and Terminal, show up with no problem.  But I cannot edit say my Office icons or anything.  Any help?  Thanks!

---

### Post by jISh on 2006-08-30
Have you updated your system since installing it?
XFCE had some nasty menu editor bugs before it was patched!
Just pop open a terminal and enter the following:
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by nazgulord on 2006-08-30
Wouldn't just apt-get upgrade work? Isn't dist-upgrade used only if you're upgrading (say from Breezy to Dapper)?

nazgulord.

---

### Post by DirtDawg on 2006-09-01
I've been using ".desktop" files to get around this. It's easy, actually.

Desktop files are located in /usr/share/applications.

To make a new menu entry, just create a new desktop file. For a program called "sooperoffice", for example, create a file called "sooperoffice.desktop", fill it with the proper info (use a different ".desktop" file as a template), and it will appear in the menu.

To remove a menu item, add this line to the bottom of a desktop file:```
 NoDisplay=true 
```

To change an icon, just enter the path of the new icon: ```
Icon=/usr/share/pixmaps/sooperoffice_icon.png
```

To change where a program is listed, change the "Categories" list. For example, [Cream]("http://cream.sourceforge.net/") was placed in "Applications" after I installed it, but I wanted it in "Development". So I changed the line:```
Categories=**Application**;Utility;TextEditor;
```
to:```
Categories=**Development**;Utility;TextEditor;
```

You can change other things too, just remember to make backups.
NOTE: Make backups in a different folder. I've noticed naming something like "sooperoffice.desktop_backup" sometimes prevents menu items from appearing.

Thats how I've been handling it.

---

