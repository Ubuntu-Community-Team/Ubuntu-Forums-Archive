---
title: "Missing menu items"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-06-29
I use Ubuntu 7.04. I am unable to see the following sub menus in the menu list.

    (a)    Under Applications I don't see Add/Remove Applications.....
    (b)    Under System---->Administration-------> I don't see software sources Sub menu.

Please help me locate and add these 2 menus. Under Preferences----->Main Menu also they are not listed.:(
Someone kindly guide me to add them . 
thanx in advance.

---

### Post by speaker219 on 2007-06-29
It is just a GUI to edit
/etc/apt/sources.list

---

### Post by kakalaky on 2007-06-29
You can do what both of those do in one interface using synaptics.  it's under System -> Administration

---

### Post by tarek on 2007-06-29
OK, I'm looking at my menu now, I'll copy the commads and then you can add them:

NAME
```
COMMAND
```
```
ICON
```

Add/Remove... 
```
/usr/bin/gnome-app-install
```
```
/usr/share/icons/hicolor/scalable/apps/gnome-app-install.svg
```

Software Sources
```
gksu gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```
```
/usr/share/icons/Tango/scalable/apps/software-properties.svg
```

that should do it.

tk

---

### Post by gupta_sumesh63 on 2007-06-29
Thanx TAREK
That helped.
I have them both on the menu
Sumesh:guitar:

---

### Post by avik on 2007-06-29
You can also edit the menu items by right-clicking on the main menu and choosing "Edit Menu."

---

