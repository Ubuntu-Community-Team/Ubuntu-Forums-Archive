---
title: "problem installing Google Earth and Gnome Splash screen manager"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-02-14
For Google Earth, i've downloaded this file:
GoogleEarthLinux.bin
and i get this error:
Could not open the file /home/panti/Download/GoogleEarthLinux.bin.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

For Gnome Splash Screen Manager, i've donwloaded this file:
gnome-splashcreen-manager_0.2-5_all.deb

and i get this error:
Error: Dependency is not satisfiable: libglade2-ruby

---

### Post by Maestro23 on 2007-02-14
> **panti19 said:**
> For Google Earth, i've downloaded this file:
GoogleEarthLinux.bin
and i get this error:
Could not open the file /home/panti/Download/GoogleEarthLinux.bin.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

For Gnome Splash Screen Manager, i've donwloaded this file:
gnome-splashcreen-manager_0.2-5_all.deb

and i get this error:
Error: Dependency is not satisfiable: libglade2-ruby
Open Terminal, cd to the directory you d/l the file to.

> chmod +x GoogleEarth.bin
./GoogleEarth.bin



You need to install libglade2-ruby.  Either true Synaptic or apt-get install.

---

