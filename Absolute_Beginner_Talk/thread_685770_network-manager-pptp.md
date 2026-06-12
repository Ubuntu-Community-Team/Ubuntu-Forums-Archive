---
title: "network-manager-pptp"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by manzoor on 2008-02-02
It doesnt installs when I click install package it asks for password, I entered it, then it shows up and suddenly the window vanishes :(

help

---

### Post by manzoor on 2008-02-02
bump*

---

### Post by manzoor on 2008-02-02
help please

---

### Post by manzoor on 2008-02-02
any one help ?

its also the same with html2text

---

### Post by manzoor on 2008-02-03
hello help please

It doesnt installs when I click install package it asks for password, I entered it, then it shows up and suddenly the window vanishes

help

---

### Post by manzoor on 2008-02-03
plz

---

### Post by manzoor on 2008-02-03
help please help

---

### Post by manzoor on 2008-02-03
hey yall help me out please

---

### Post by manzoor on 2008-02-03
hepl

---

### Post by manzoor on 2008-02-03
yohoo help help help me baby help help help

woa

---

### Post by lswest on 2008-02-03
what are you trying to install from? a .deb?  have you tried apt-getting it? ```
sudo apt-get install network-manager-pptp
```  you may need some other sources for that, but otherwise, it should be fine.  Also, are you sure you have all the dependencies for the package installed?

---

### Post by manzoor on 2008-02-03
yes im installing for a .deb

i cant install from apt-get as I dont have internet connection

and yeah when installing from the the deb the status says " All dependencies are satisfied" so this means that I have the dependencies



GRrrrrrrrrrrrrrrrrr this network connection is provoking to uninstall Ubuntu lol its so hard

---

### Post by manzoor on 2008-02-03
is there any way to install the package i have downloaded, from the terminal ?

Can't I install the deb file I have downloaded with the terminal /

---

### Post by lswest on 2008-02-03
do you not have an internet connection at all, or is it just not working? it would be a helluva lot easier if you had internet :P [this page]("http://packages.ubuntu.com/gutsy/net/network-manager-pptp") has a list of dependencies...just take a double-checking of your packages to see if you have everything:P otherwise, the problem may be with dpkg, and might be solved in an update :P if you can, just hook it up with an ethernet cable for a bit and update all the stuff, then try again.

and yes, you can install the package from the terminal, i'm just gonna have a quick look on what the exact syntax is.

all right, so the command to install from the terminal is ```
sudo dpkg -i [name of package].deb
```

---

### Post by manzoor on 2008-02-03
i have internet connection but I can't access it from Ubuntu, its not working there :( cuz i havent configured it yet and to set it up i need pptp which is the prob

---

### Post by manzoor on 2008-02-03
you know there are hell alot of dependencies to install

and each one requires its own dependency 

if there is no other way im gonna uninstall it thanks

---

### Post by lswest on 2008-02-03
well, hopefully the above will help^^ (i was editing my post instead of double-posting :P)

also, most of the dependencies for that file were probably installed with ubuntu for default, as they're pretty important:P

---

