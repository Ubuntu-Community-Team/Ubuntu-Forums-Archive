---
title: "Could you explain this error message plz"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by zanazzi on 2007-07-08
```
(Reading database ... 
dpkg: serious warning: files list file for package `secondlife-install' missing,
 assuming package has no files currently installed.
89973 files and directories currently installed.)
Preparing to replace secondlife-install 1.17.0.12-1~getdeb1 (using .../secondlif
e-install_1.17.0.12-1~getdeb1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p
rocess: Resource temporarily unavailable
dpkg: error processing /home/phillip/Desktop/secondlife-install_1.17.0.12-1~getd
eb1_i386.deb (--install):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /home/phillip/Desktop/secondlife-install_1.17.0.12-1~getdeb1_i386.deb

```

i think i know what happened, it says in the transcript that something else was using the dpkg (whatever that is)

so new question how do i find out what is using it and stop it?

---

### Post by dmfield on 2007-07-09
dpkg is the software which is installing your .deb file.
Its possible the file wasn't downloaded corrdctly

however try

> sudo apt-get -f install to forse the install

---

### Post by az on 2007-07-09
> **zanazzi said:**
> (Reading database ... 
dpkg: serious warning: files list file for package `secondlife-install' missing,
 assuming package has no files currently installed.


This is an improperly built package.  Stay away from these.


> **zanazzi said:**
> 
89973 files and directories currently installed.)
Preparing to replace secondlife-install 1.17.0.12-1~getdeb1 (using .../secondlif
e-install_1.17.0.12-1~getdeb1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p
rocess: Resource temporarily unavailable

If the package manager is running, then you cannot install packages by hand until it's finished.

> **zanazzi said:**
> (
dpkg: error processing /home/phillip/Desktop/secondlife-install_1.17.0.12-1~getd
eb1_i386.deb (--install):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /home/phillip/Desktop/secondlife-install_1.17.0.12-1~getdeb1_i386.deb


You tried to install this deb from your desktop, probably by running 
sudo dpkg -i secondlife-install_1.17.0.12-1~getdeb1_i386.deb 
from your Desktop (ok clicking on it and trying to install it with GDEBI)

---

