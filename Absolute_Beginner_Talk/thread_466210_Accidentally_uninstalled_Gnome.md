---
title: "Accidentally uninstalled Gnome"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Charlie Chick on 2007-06-06
Hello Everybody,

It´s a long story, but I accidentally uninstalled Gnome from my laptop running 7.04. I´m away from home and therefore don´t have access to my Ubuntu disc. 

The computer boots OK, but after I login, instead of Nautilus coming up and all the applications showing, I get a brown screen. I can, however, get to a command line.

My question is, can I reinstall Gnome from the command line, without my disc and without a working internet connection?

Thanks!

---

### Post by Ferri on 2007-06-06
What do you exactly mean by uninstall GNOME? What did you did?
If you really uninstalled GNOME you will need an internet connection (or the CD).

---

### Post by Charlie Chick on 2007-06-06
I was uninstalling some media files and it also uninstalled Open Office and Gnome. I didn´t believe that it would actually uninstall Gnome, as this happened to me once before and Gnome remained.

Are the Gnome files not sitting on the hard drive somewhere? After all, when you use Synaptic, you can choose to uninstall or remove permanently. If you just choose to uninstall, you can re-install later without having to download any more files.

Is there not some command line I can use to reinstall Gnome? I can`t get to Synaptic, so it has to be from X.

Ironiaclly, I have an ISO image of the 7.04 installation disc on my hard drive, but I can´t access it to burn a fresh disc. Or can I? Is it possible to burn a fresh disc from the command line?

---

### Post by digitalbenji on 2007-06-06
if you have a network connection, you can do:
sudo apt-get install gnome
and that will do it.

---

### Post by handaxe on 2007-06-06
```
wodim dev=/dev/cdrw driveropts=burnfree,noforcespeed fs=14M speed=10 -dao -eject -overburn -v something.iso
```Replace /dev/cdrw as appropriate and of course, something.iso. "wodim -h" and "man wodim" for help.

HA

PS: if gnome was **updated** since the primary install, then yes, the debs will be archived (if you set that option). However, Feisty seems not by default to install all the packages in gnome, and so ```
sudo apt-get install gnome
``` will likely want to download a slew of new files.

PS: there are bug reports abroad about wodim but see if it flies.  Other option is "cdrdao". "cdrdao write -help" will provide well, help as will man etc

---

### Post by strabes on 2007-06-06
sudo aptitude install ubuntu-desktop

---

### Post by Charlie Chick on 2007-06-07
Thanks, Strabes, your tip worked beautifully, althought I had to pinch a working internet connection at an Internet Cafe!

---

