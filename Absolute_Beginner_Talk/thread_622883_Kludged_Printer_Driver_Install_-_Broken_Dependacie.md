---
title: "Kludged Printer Driver Install - Broken Dependacies"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by the_cog on 2007-11-25
I went to install my Brother printer and installed the cups wrapper before the lpn.  Now my synaptics  is hosed for some reason.  this is what I get in synaptic:

E: The package mfc5460cncupswrapper needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

and in terminal:

:~$ sudo apt-get remove --purge mfc5840cnlpr
[sudo] password for cog:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package mfc5460cncupswrapper needs to be reinstalled, but I can't find an archive for it.

:~$ sudo apt-get remove --purge mfc5460cnlpr
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package mfc5460cncupswrapper needs to be reinstalled, but I can't find an archive for it.

:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package mfc5460cncupswrapper needs to be reinstalled, but I can't find an archive for it
.
:~$ sudo apt-get remove --purge mfc5460cnsupswrapper
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package mfc5460cncupswrapper needs to be reinstalled, but I can't find an archive for it.

Any help would be greatly appreciated.

---

