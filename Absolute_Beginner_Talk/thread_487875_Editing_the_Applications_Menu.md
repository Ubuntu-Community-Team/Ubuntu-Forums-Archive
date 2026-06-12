---
title: "Editing the Applications Menu"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by muteki on 2007-06-29
I would like to be able to somehow change the layout of the standard "Applications" menu in Xubuntu.  Right-Clicking on on the menu and choosing "Edit Menu" does bring up a menu editor of sorts, but does not allow any changes to the default menu really.

Installing some programs have caused some of them to create multiple unnecessary folders such as "Education" and "Science" when the apps could go in the same folder.  Could someone point me to something that would allow me to move things around without making a whole new menu, or show where the config file would be (assuming there is one)

Thanks!

---

### Post by ronocdh on 2007-06-29
IIRC, in regular Ubuntu there is something called the "Ala Carte Menu Editor." Perhaps this is installable via Add/Remove programs or Synaptic? HTH.

---

### Post by muteki on 2007-06-29
Unfortunately that only seems to work for gnome's menu, not Xfce's.  It would be nice if it did, however, because it works a lot better than the one that comes with xubuntu.

---

### Post by fifafrazer on 2007-06-29
I remember editing some config text files, which the application menu is generated from, but i dont remember where to find them.

---

### Post by kadath on 2007-06-30
To edit Xubuntu's main menu, you need to edit the .desktop files for the relevant apps that you want to move (or remove).

The system-wide .desktop files can be found in /usr/share/applications/.

The files look something like this:

```
[Desktop Entry]
Encoding=UTF-8
Name=foo
GenericName=bar
Comment=Best program ever
Exec=foobar
Icon=/usr/share/pixmaps/foobar.xpm
Terminal=false
Type=Application
Categories=Multimedia;

```

You can move items between categories by changing the values in the "Categories" section of each .desktop file. You might want to examine some of the .desktop files to get an idea of how it works.

If you want to remove a program from the menu, just add this line to the bottom of its .desktop file:

```
NoDisplay=true
```

To edit the .desktop files easily, open a terminal and type:

```
sudo thunar
```

and then navigate to /usr/share/applications/. There, you can open .desktop files using mousepad.

---

