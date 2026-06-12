---
title: "cant install packages through terminal"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-03-12
i try to install allot of things and until now i dont have any success .
the last on was: "

fanny@fanny-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fanny@fanny-desktop:~$ sudo apt-get install gstreamer0.10-plugins-ugly
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.10-plugins-ugly is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-plugins-ugly has no installation candidate
fanny@fanny-desktop:~$ sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.10-plugins-ugly-multiverse
fanny@fanny-desktop:~$

---

### Post by ohzopants on 2007-03-12
It looks like you have a problem with your repositories.  This site has excellent information about updating your sources files as well as clear instructions for setting up many things in ubuntu:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)

---

### Post by fanny on 2007-03-12
i tried also through synaptic and get a error message

---

