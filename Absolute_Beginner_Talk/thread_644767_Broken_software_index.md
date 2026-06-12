---
title: "Broken software index"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Bianchi165 on 2007-12-19
Hi, getting errors when trying to upgrade 7.10 or install new programs.
New install do not think I could have messed it up to bad already.
A couple of screen shots with errors attached, let me know if you need any thing else.

1st screen shot shows error while trying to add program 


second screen shot when trying to update get this error ran instructions but get error second screen shot shows error
-------------------
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first
--------------------

Thank you in advance for looking.

---

### Post by tehet on 2007-12-19
Try running
```
sudo apt-get clean
```
and see if that solves it.

---

### Post by rsambuca on 2007-12-19
Open a terminal and run the following:
```

sudo apt-get install -f
sudo apt-get dpkg --configure -a
```

Then if those produce no further errors,

```
sudo apt-get update && sudo apt-get upgrade
```

Then try and install your packages.

---

