---
title: "Lightscribe software RPM package"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-05-17
I have lightscribe-1.6.43.1-linux-2.6-intel.rpm on my desktop, as RPM can i run it in ubuntu?

---

### Post by taurus on 2007-05-17
You need to use alien to convert it to .deb and install it with dpkg.

```
sudo aptitude update
sudo aptitude install alien 
alien lightscribe-1.6.43.1-linux-2.6-intel.rpm
sudo dpkg -i lightscribe-1.6.43.1-linux-2.6-intel.deb
```

---

### Post by Emerzen on 2007-05-17
A quick hijack as I'm in the same boat as mojo123.  On the lighscribe website it says this version is not compatible w/ Ubuntu.  If we go this route to install (fine if it doesn't work) but could it break my system?  In other words, will dpkg watch out for dependencies the way apt-get does?  thanks.

---

### Post by mojo123 on 2007-05-17
i installed it through the debian package (btw thanks, now i can use alien) but it appears that its not in my application bar? How can i add it to Graphics?

---

### Post by Emerzen on 2007-05-17
Go to:

System->Preferences->Main Menu

A window will open w/ 2 panes, highlight the Graphics tab on the left and then hit the Add button on the right->Name it, put the command to run the program in the "command" box preceded by gksudo.  Add an icon if you like.  When done close it up and it should now be in your menu.

---

