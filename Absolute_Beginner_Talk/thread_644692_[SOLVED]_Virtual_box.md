---
title: "[SOLVED] Virtual box"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by discoade on 2007-12-19
hi 
im trying to install virtualbox but i i get an error.

ive downloaded the correct file but when i try to install i get this..
```
adrian@adrian-desktop:~$ sudo dpkg -i virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb
[sudo] password for adrian:
Selecting previously deselected package virtualbox.
(Reading database ... 128337 files and directories currently installed.)
Unpacking virtualbox (from virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb) ...
dpkg: dependency problems prevent configuration of virtualbox:
 virtualbox depends on libxalan110; however:
  Package libxalan110 is not installed.
 virtualbox depends on libxerces27; however:
  Package libxerces27 is not installed.
dpkg: error processing virtualbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 virtualbox
adrian@adrian-desktop:~$ 
```i assume its a dependency problem but what packages do i need to get the proper files?

---

### Post by LinuxIsInnovation on 2007-12-19
virtualbox depends on libxalan110; however:
  Package libxalan110 is not installed.
 virtualbox depends on libxerces27; however:
  Package libxerces27 is not installed.

Its mentioned in your output :)

---

### Post by discoade on 2007-12-19
so do i just install them through synaptic?

---

### Post by AndyCooll on 2007-12-19
VirtualBox itself is actually in the repositories. Have you tried the route of installing the whole app using Synaptic instead yet?

:cool:

---

### Post by discoade on 2007-12-19
yes it says....
virtualbox:

Package virtualbox has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

??? it was the first thing i tried!

---

### Post by discoade on 2007-12-19
ok i installed the libxalan110 file and it installed the other one along side it vbox in installed and working   many thanks

---

