---
title: "Wine desinstallation"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by linuxrock on 2008-01-11
I'm new to linux so i had wine install since i didn't know much about it.But since i found all program needed in linux i decide to uninstall wine but the program on wine won't dissapeared.They always show in my application with a wine folder.Any idea how can i remove it? Thanks for your help!:guitar:

---

### Post by Amstell on 2008-01-11
hit up the synaptic manager....uninstall it there and delete it from the applications menu.  I would also suggest deleting the folder /home/NAME/.wine

you may have to hit ctrl+h to see it but that will have a whole **** load of stuff.

CHeers

---

### Post by linuxrock on 2008-01-11
I did not find your (name) folder but i found  .wine and i have deleted it but its still showing in my application folder and wine is also deinstall from the synaptic package manager.

---

### Post by swoll1980 on 2008-01-11
Try ```
sudo dpkg -P wine
```

---

### Post by FreewheelinFrank on 2008-01-11
I deleted Wine recently, but I can't remember how I got rid of the menu items.

Possible it was through System>Preferences>Main Menu.

Right clicking menu items there gives you an option to delete.

---

