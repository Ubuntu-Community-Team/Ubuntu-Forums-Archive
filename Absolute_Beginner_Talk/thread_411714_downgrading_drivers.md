---
title: "downgrading drivers"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by colinireland on 2007-04-17
Hey everyone.

Can anybody tell how to downgrade my ipw2200 drivers? I tried installing the new drivers and firmware to inable packet injection on my card but made a mess of it and can't connect to the internet. I don't want to have to wipe my laptop and reinstall Ubuntu 6.06 LTS just to be able to connect to the net.


Any help would be greatly appricated.

Colin

---

### Post by bwhite82 on 2007-04-17
Assuming you have a repository enabled that contains the older version, it should be as simple as opening up Synaptic, searching for the name of the driver package, highlighting it, then Package>Force Version. Find the older version in the combo-box and you're good to go.

---

### Post by chili555 on 2007-04-17
Did you install the new drivers from source code, that is, a .tar.gz file? It should be as simple as *sudo make uninstall* from the directory you installed from. If the install loaded the firmware at the same time, then it should be removed by uninstall. 

Another option is to straighten out your install. All of us have fumbled an install a few times; we'd be happy to help you learn from our mistakes.

You could also boot into a previous kernel and ask Synaptic to reinstall all the relevant 2.6.17-11 stuff, image, headers and restricted modules.

---

### Post by Austin_KW on 2007-04-17
"lsmod" will tell you what drivers are installed 
You can remove a module from a running kernel with "modprobe -r moduleName"

The install process just copies the moduleName.ko to the /lib/module/ for your kernel version
"locate ipw2200" will show you where it is installed, you can remove/replace it
"depmod -a" will update dependancies
"modprobe ipw2200" will then install the new version

---

