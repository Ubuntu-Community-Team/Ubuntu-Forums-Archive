---
title: "[SOLVED] Firefox Woes in Kubuntu"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by vertexoflife on 2007-11-26
I tried to go into my .mozilla/firefox/ and just copting and pasting bookmarks and plugins into there, as this has worked for me before. However, firefox no longer ran: I got the dialog "Firefox is already running...etc" While it was not running, so I uninstalled meaning to reinstall, and now it does not want to install at all.

```
brian@brian-laptop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox has no installation candidate
brian@brian-laptop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox has no installation candidate
brian@brian-laptop:~$ sudo aptitude install firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for firefox
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
brian@brian-laptop:~$                                       
```

---

### Post by Inxsible on 2007-11-26
Search the Synaptic for Firefox. Maybe the package name is suffixed with the version 2.0.0.9 or something.I don't remember for sure. 

When you are in doubt of a package name, it is always better to search synaptic and install from there.

---

### Post by vertexoflife on 2007-11-26
Sorry, I forgot to mention that installing firefox through synaptic does not work either. I click on request install, but nothing happens at all.

---

### Post by vertexoflife on 2007-11-26
Not sure what happened, but updating the sources.list and then installing worked. oO

---

