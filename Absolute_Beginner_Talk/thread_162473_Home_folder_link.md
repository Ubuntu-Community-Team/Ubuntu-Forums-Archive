---
title: "Home folder link?"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-19
how can I get an icon on my taskbar that is an icon of "Home" so when i click it it open home folder?  I try and drag/drop home folder on it but it doesnt work...

---

### Post by htinn on 2006-04-19
Just create a custom launcher that performs this command:

nautilus /home/user/

---

### Post by Sutekh on 2006-04-19
Open :

Applications Menu - System Tools - Configuration Editor

Expand :

apps - nautilus - desktop

Then check :

**home_icon_visible**

---

### Post by x5452 on 2006-04-19
cool, awsome thanks...do you know how I can get it to act with my icon theme now?  I have like the tango and crystal svg cool icons...but how do i get that new launcher to play nice with the pretty icons??

---

### Post by htinn on 2006-04-19
Right-click the icon and select "Properties" then click on the icon button. That lets you change the icon to whatever you want it to be.

---

### Post by x5452 on 2006-04-19
ok im lost, i know ive had it before.  if i go to the nautilus thing and click show icon it put it on the desktop, and wont let me drag it to the panel.  If i right click on the custom launcher to change the icon there is no selection for the home icon. if i browse and send it to the folder where i have downloaded my icon themes, it still does not let me use any of them for the icon.

Edit: sorry I am a moron, I was trying to drag it from the places menu like last time but was clicking the right toiuchpad button instead of left.  oops

---

### Post by htinn on 2006-04-19
The arbitrary "Home" icon is only available on the desktop. That is why you should never actually use it. Use a custom launcher instead. I don't know if you can drag custom launchers between the desktop and the panel (as I never actually use the desktop for anything).

As for icons, the folders you can usually find them are:

/usr/share/pixmaps/
/usr/share/icons/hicolor/48x48/apps
/usr/share/icons/gnome/48x48/apps

Some packages put icons in random locations (like /usr/local/share/pixmaps), so you may want to perform this first:

dpkg -L packagename

Take take of where the png, svg and xpm files are.

EDIT: One more place you might look for icons:

~/.icons

---

### Post by bollix47 on 2006-04-19
Applications - Accessories - <right click on> File Browser - <select> Add this launcher to panel

---

### Post by mostwanted on 2006-04-19
There is a much easier way to do this. Open gconf-editor and go to

> apps &#8594; nautilus &#8594; desktop

Then tick the option that says *home_icon_visible*. Gives you a nice icon and all.

---

