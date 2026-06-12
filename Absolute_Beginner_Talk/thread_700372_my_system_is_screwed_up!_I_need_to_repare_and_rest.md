---
title: "my system is screwed up! I need to repare and restore lost files"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by thesqudge on 2008-02-18
Ok so i think my system is screwed up i used synaptic to install and uninstall a milllion different things, most of which i had no clue to what they did, i was really just trying to install beryl, then uninstall it then install it again, the install kde then uninstall it, then install it again the uninstall it again, and somewhere along the way i uninstalled gnome somehow and now my system is crazey screwed up. I have no window borders, i cant use the terminal to install things i think or even uninstall things i'm pretty sure, i keep getting cryptic error messages and more. I just need a way to restore my ubuntu back to it's original state.

---

### Post by justleen on 2008-02-18
try this in a terminal
```
 sudo apt-get --reinstall ubuntu-desktop 
```

should nicely rebuild the gnome desktop

---

### Post by randy78 on 2008-02-18
Yes, it's easy to go crazy on installing everything you can get your hands on ;)

do this in a terminal:
metacity --replace

Then log out and log-in again...

Open up a new terminal and do 
sudo dpkg-reconfigure xserver-xorg

Let us know!

---

### Post by thesqudge on 2008-02-18
it said invalid opertion ubuntu-desktop

---

### Post by randy78 on 2008-02-18
Also, from the login screen, you have the option of choosing which Session you want to use...
I.E. Gnome, KDE etc...

When you are at the login screen, hit options, and select your session...

You may have accidentally set another Desktop Environment as the default...

---

