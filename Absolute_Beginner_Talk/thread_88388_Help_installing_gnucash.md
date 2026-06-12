---
title: "Help installing gnucash"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by blroth on 2005-11-10
I have installed Breezy 5.10 and went to Synaptic to install gnucash.  The installation seemed to go well, but I can't find the application.  After searching, I found the gnucash folder in the user/share folder.  My problem is (because I am new to Linux) what do I do now to access and use the program? Help me please!  Thanks!

---

### Post by Manny C on 2005-11-10
You can access it from a terminal or from the konsole. Irrespective of which, simply issue this command at the command line to start gnucash:
```
 gnucash 
```

If you are using Gnome, you may need to issue the following at command line:
```
 killall gnome-panel 
```

This refreshes the menu items and (hopefully) will produce the gnucash program item.

If you are using KDE, logout and then login again.

---

### Post by popeye on 2005-11-10
Hi,

I installed gnucash also, i got help from more places but a howto to install it in Ubuntu is:

[http://help.ubuntu.com/starterguide/C/ch03s04.html#id2527799](http://help.ubuntu.com/starterguide/C/ch03s04.html#id2527799)

Good luck

---

### Post by gw90se on 2005-11-10
I had to use SMEG to add Gnucash to my Applications menu. It didn't install in the menu like it did in Hoary.

---

