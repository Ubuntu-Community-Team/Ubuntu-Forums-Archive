---
title: "subprocess post-installation script ......error"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Delirious on 2007-07-01
I had installed quodlibet with apt-get and then removed it with apt-get and now whenever i installed something (wine in this case) i get these errors even though im not trying to install it.

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

and

 subprocess post-installation script returned error exit status 1


```

root@Ubuntu1:~# aptitude install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  wine 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.1MB of archives. After unpacking 46.8MB will be used.
Writing extended state information... Done
Get:1 http://wine.budgetdedicated.com feisty/main wine 0.9.39~winehq0~ubuntu~7.04-1 [10.1MB]
Fetched 10.1MB in 29s (345kB/s)                                                                     
Selecting previously deselected package wine.
(Reading database ... 121914 files and directories currently installed.)
Unpacking wine (from .../wine_0.9.39~winehq0~ubuntu~7.04-1_amd64.deb) ...
Setting up python-mutagen (1.10.1-0ubuntu2) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/mutagen/__init__.py
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/mutagen/__init__.py
dpkg: error processing python-mutagen (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of exfalso:
 exfalso depends on python-mutagen (>= 1.4); however:
  Package python-mutagen is not configured yet.
dpkg: error processing exfalso (--configure):
 dependency problems - leaving unconfigured
Setting up wine (0.9.39~winehq0~ubuntu~7.04-1) ...

Errors were encountered while processing:
 python-mutagen
 exfalso
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python-mutagen (1.10.1-0ubuntu2) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/mutagen/__init__.py
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/mutagen/__init__.py
dpkg: error processing python-mutagen (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of exfalso:
 exfalso depends on python-mutagen (>= 1.4); however:
  Package python-mutagen is not configured yet.
dpkg: error processing exfalso (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-mutagen
 exfalso
root@Ubuntu1:~# 


```

---

### Post by Delirious on 2007-07-01
sorry, never mind, had to go into synaptic and completely remove the offending package.

---

