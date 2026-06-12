---
title: "where is gnome magnifier file located in Ubuntu 7.10"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by RoBo5050 on 2008-02-14
Hello forum members,
   I have Ubuntu 7.10 successfully installed on a Biostar #P4M800Pro-M7 motherboard-based desktop computer,and have recently used the update service built into 'Gnome;I found out that the Gnome-Magnifier was updated,but would like to create a Launcher for it,and do not know where to look for the gnome app file!!:confused:

If anyone knows where-either by terminal or file manager-the Gnome-magnifier file is located,I would greatly appreciate a reply!!

---

### Post by agurk on 2008-02-14
```
$ apropos magnifier
magnifier (1)        - GNOME Magnifier (gnome-mag)

$ locate magnifier
/usr/share/man/man1/magnifier.1.gz
/usr/bin/magnifier
```
Hope it helps.

---

### Post by ubuntu27 on 2008-02-14
I am not in my home now, so I am not using GNU/Linux now.

Open-up Synaptic Package Manager and search for "magnifier" 
Find the package you are looking for. 
Select the package and click on Properties.
A new window should open. Click on installed Files. See what files has been installed with the package. The one you want is most likely to be inside the "bin" directory.

---

