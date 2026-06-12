---
title: "How?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Andeh333 on 2007-03-18
Lets say i used apt-get to get a program in the terminal, that goes fine and it installs.. how do i make it show up in the applications menu?

---

### Post by eljalill on 2007-03-18
You could reboot, and that should do the trick...
The aplications menu takes a while to update after installation of new programs, but they should show up there eventually. Meanwhile you can start them form the terminal (just type the program name), if you want to check on them or use them.

---

### Post by AtrejuT on 2007-03-18
depends on what you installed. usually, if it is a programme with a GUI it should show up automatically. If not, you can use the menu entry *system-preferences-Main Menu* to add entries to the menu.
You'll then need to know the command that starts the programme you installed, usually that is just the same as the name of the programme.

---

### Post by Kobalt on 2007-03-18
If it doesn't automatically, you have many options. You can also open the menu editor alacarte (if you don't find it either in the menus press Alt+F2 then enter 'alacarte') and search for your program... If it's not there you can create a launcher afterwards...

---

### Post by Andeh333 on 2007-03-18
Ok then thanks.

---

### Post by Atreus12 on 2007-03-18
If your panel just needs a refresh you can do the following 

```
killall nautilus
```

```
killall gnome-panel
```

and it will refresh them

---

### Post by McMarley on 2007-03-18
oh geez...
some of my programs on the panel dont work, i just click on them and the list disappears and nothing.
also in system--admin, theres opposed to be a printers line where i can config the settings, and ts just not there!
i would need some explanations plz

---

