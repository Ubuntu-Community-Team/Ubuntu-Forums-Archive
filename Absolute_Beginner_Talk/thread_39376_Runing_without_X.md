---
title: "Runing without X"
date: 2005-06-04
forum: Absolute Beginner Talk
---

### Post by seekyrr on 2005-06-04
Got an old K2-450 to run ubuntu, but I am finding the GUI way to slow.  I mainly wanted it for Nessus, ftp and other command line apps.

Ive been away far to long from linux and can't remember how you boot without going into X.

Any help would be much appreciated.

Seek

---

### Post by lovebug356 on 2005-06-04
I think :
sudo apt-get remove xorg

This removes all GUI-stuff from your system.

---

### Post by az on 2005-06-04
You can remove gdm and that will boot you into a console.  You will still be able to start x by running startx,

You can boot into a runlevel that does not start up gdm.  Pass a number to the kernal at boot and that is your runlevel.

There are many ways.  GDM is what starts up X in Ubuntu.

---

