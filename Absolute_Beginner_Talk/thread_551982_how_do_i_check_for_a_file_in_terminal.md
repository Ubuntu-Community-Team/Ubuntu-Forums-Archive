---
title: "how do i check for a file in terminal ?"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by mike_m on 2007-09-15
I'm trying to install glipper-1.0 & am missing a Dependant but don't know which one, I got a list & would like to use the terminal to check, can that be done?

My list is this: libatk1.0-0 (>= 1.13.1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.4.2), libfontconfig1 (>= 2.4.0), libglib2.0-0 (>= 2.12.9), libgtk2.0-0 (>= 2.10.3), libpango1.0-0 (>= 1.16.2), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxrandr2 (>= 2:1.2.0), libxrender1, python-gtk2, python-gnome2, python-gnome2-desktop

The thing is I got this glipper v1.0 to install & run fine on my laptop, but not on my desktop. (I don't use the desktop as much)

Point: this is a new glipper so it's not in the repositories yet, unless there are some secret ones ;)

Thanks!

---

### Post by st33med on 2007-09-15
Do:
```
apt-get install <program> -s
```
for each. This will simulate installing the program, so if it 'acts' like it is installing, then that is your package you're missing.

Sloppy way of doing it. You could also check Synaptic Package Manager and search for those packages.

---

### Post by Hospadar on 2007-09-16
you might try installing it from the repositories to see if that does does the dependancies. then uninstall the package and reinstall your software.

---

### Post by mike_m on 2007-09-16
Thanks, I had been getting 0 hits on searches in synaptic on some items, I think the names were incomplete, & they are parts of larger packages.

Anyways this is **Solved**   the trick was to delete the old .glipper folder (I had v0.95 installed, & the complete uninstall from synaptic didn't delete that folder) the install for v1.0 wont over write it.

guess I did have all the  Dependencies.

Thanks again for the help.

---

