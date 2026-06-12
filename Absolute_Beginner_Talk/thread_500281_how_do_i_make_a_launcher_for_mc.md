---
title: "how do i make a launcher for mc"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by rhendrix9 on 2007-07-13
I installed MC (Midnight Commmander) using ;
sudo aptitude install mc

so 1. I can't even figure out where it is
2. how do I make a laucnher (I assume that's what I call it) for it

right now I can start a terminal window and type in mc and it runs. Would this mean it can't run in a gui environment? If this is the case does anyone know of something similar that will run in a gui from the desktop?
tia

---

### Post by felicity on 2007-07-13
I don't think Midnight Commander is a GUI program, just console. I could be wrong though, I've never used it.
[URL="http://www.obsession.se/gentoo/"]
Gentoo File Manager[/URL] is something that has a GUI and looks similar to it.

---

### Post by annda on 2007-07-13
1. in the terminal: whereis mc

2. command is mc, type is "application in terminal"

this should work.

---

### Post by Patrick K on 2007-07-13
You can make a launcher. To put in in the menus, right click on the menus and select "edit menus". Select the menu you want it in and select "New Item". Fill out the boxes and put "mc" [without quotes] in the command box. Check the box "Run command in a terminal". Close up and it should run from the menus. You may need to restart X. I often do.

For a panel launcher right click the panel and select Custom App Launcher. Fill in the boxes as above except click on "Type" and choose "Application in Terminal".

For one on the desktop, right click on an open space, select Create Launcher. This dialog is the same as the panel dialog.

---

