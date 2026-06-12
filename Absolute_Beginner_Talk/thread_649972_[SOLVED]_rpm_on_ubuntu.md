---
title: "[SOLVED] rpm on ubuntu ?"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by neoragexxx on 2007-12-25
is it possible to install/use rpm files on ubuntu ? cause i have a software only in rpm installation mode..(e.g informix dynamic server)

thanks in advance:)

---

### Post by taurus on 2007-12-25
You can use alien to convert the .rpm to .deb and then install it with dpkg.

```
sudo apt-get update
sudo apt-get install alien
alien **filename.rpm**
sudo dpkg -i **filename.deb**
```

---

### Post by SOULRiDER on 2007-12-25
Yes, but its a terrible idea. Are you sure there are no debs around? Cant you compile from source?

If you REALLY REALLY REALLY need to use RPM you will have to install Alien.

---

### Post by wormser on 2007-12-25
It is best to install from the repositories or from a .deb.  I would think to install from source would be third best.  You can convert .rpms to .debs with alien.  What are you trying to install?

```
sudo apt-get install alien
```

---

### Post by neoragexxx on 2007-12-25
great thanks for the replies guys!

p.s: i am trying to install informix dynamic server and i don't have the source code.

---

### Post by RomeReactor on 2007-12-25
Hi. You can install **Alien**, a command line program that lets you install from RPM packages or convert them DEB; look for it in Synaptic, or from the terminal:
```
sudo apt-get install alien patch bzip2 lsb-rpm lintian
```

Once it's installed you use it like this (first change directory to where your RPM file is):
```
sudo alien -i PACKAGE_NAME.rpm
```
to install from RPM; or
```
sudo alien -d PACKAGE_NAME.rpm
```
to convert the RPM to DEB.

EDIT: Toooo sloowww....

---

