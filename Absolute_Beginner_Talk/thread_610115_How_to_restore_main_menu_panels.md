---
title: "How to restore main menu panels?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-11-11
Somehow I killed the Main Menu Panels, and would like to retore all of them -- Applications Panel, System, Places, etc.  How can I do that?

I am an utter beginner.  Please give me every single step in excruciating detail so I can follow the breadcrumbs.  TIA

---

### Post by mkoehler on 2007-11-11
Did you kill the panels or just the menus?

---

### Post by carlosjuero on 2007-11-11
Did you lose the whole top bar? Or just the items in it?

For just the items do this:

Right click the bar
Select 'Add to Panel'
For the Applications, Places, and System menus click on 'Menu Bar' and click the Add button

Do the same thing for the Date display, System Tray, and anything else you had up there.

---

### Post by carloslosgrande on 2007-11-11
[FONT="Comic Sans MS"]If its the main menu, go to[COLOR="#0000ff"] system>preferences>main menu[/COLOR] and try [COLOR="Blue"]revert[/COLOR], or just re-select the items you want on the menu[/FONT]

---

### Post by spupy on 2007-11-11
IIRC, there should be a package called ubuntu-default-settings or something like that. At least for xubuntu there is such package. (Can't find it right now cause I'm not at ubuntu)

---

### Post by bettyhills on 2007-11-11
I did have the bar but no panels.  Thank you.  This is the answer.

Right click the bar
Select 'Add to Panel'
For the Applications, Places, and System menus click on 'Menu Bar' and click the Add button

---

### Post by komputes on 2007-12-13
I had the same problem with flimsy panels. Please try this:

Alt+F2

from here you have a choice of which terminal you want to use, the default is **gnome-terminal** (which is a bash terminal) or you can also use **xterm** as well.

Once you have a terminal window open it is pretty simple to restore the default panels (as they were when you first installed Ubuntu). In the terminal type:

```
sudo debconf gnome-panel
```

Reboot and enjoy the default panels, as if you just installed Ubuntu.

:popcorn:

---

