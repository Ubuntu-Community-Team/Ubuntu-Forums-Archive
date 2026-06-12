---
title: "[SOLVED] Problems with aMSN"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by DaveyG on 2007-03-18
Hi, i downloaded aMSN from Autopackage, changed the file permissionss, try to install but get an error:

```
Checking for required C library versions ... OK
Checking for X ... OK
Checking for TCL Scripting Language ... failed
-------------------------------
Error: Could not find 'TCL Scripting Language'. Try using the native package manager for Ubuntu 6.10 (apt-get) to install a package with similar name to 'tcl'. 

Error: Unable to prepare package AMSN MSN client.


```

Would anyone know how to resolve this problem?

Many thanks, Davey

---

### Post by Sam Clemens on 2007-03-18
Try installing tcl8.0 with synaptic or in a terminal running:

sudo apt-get install tcl8.0

Maybe it will then ask you for other stuff.

A better option might be to download a new aMsn package from here:

[http://www.getdeb.net/category.php?id=2](http://www.getdeb.net/category.php?id=2)

---

### Post by Fataltragedy2 on 2007-03-18
Go to synaptic package manager, type in tcl in the search, TCL 8.4 should come up aswell as TK-8.5, mark them for installation and click apply. Relaunch the .deb.

---

### Post by dmsynck on 2007-03-18
If you install aMSN from the repositories using synaptic, shouldn't the dependencies be automatically installed as well ?

---

### Post by DaveyG on 2007-03-18
Thank you so much for your help, its all solved :)

> Try installing tcl8.0 with synaptic or in a terminal running:

sudo apt-get install tcl8.0

Maybe it will then ask you for other stuff.

A better option might be to download a new aMsn package from here:

[http://www.getdeb.net/category.php?id=2](http://www.getdeb.net/category.php?id=2)

---

