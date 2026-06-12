---
title: "login screen resolution"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by steviecee on 2005-11-19
This is not serious but its bugging me - please help

When I installed ubuntu I think I selected a screen resolution that is incompatible with my fat scren monitor.

I can see the screen to login bug it has this annoying flickering at the top and bottom of the screen.

I have changed the resolution successfully within my desktop once I have logged on.

---

### Post by moffa on 2005-11-19
Not sure about this one, but since no one replied you could try :

"sudo dpkg-reconfigure -phigh xserver-xorg" without the quotes and manually setup for resolution and refresh rates.  Since you have a flat screen I doubt you can use a refresh rate higher than 60Hz.

---

### Post by steviecee on 2005-11-19
moffa

when I do this, I get the following:

Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed

---

### Post by darkmatter on 2005-11-19
[QUOTE=steviecee]moffa

when I do this, I get the following:

Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed[/QUOTE]

You made a typo...the xserver-org should be xserver-xorg

---

