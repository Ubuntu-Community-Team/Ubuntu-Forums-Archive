---
title: "Cannot load software now that I installed Gusty"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by popuptarget on 2007-10-19
If I try to add any applications I can download them, Start to install them then I get this error.  

E: tzdata: subprocess post-installation script returned error exit status 10
E: util-linux: dependency problems - leaving unconfigured

Is there a way to fix this.

---

### Post by whistlerspa on 2007-10-19
It's been a while since I've had problems with Synaptic but it looks like maybe you've got some broken packages.

If you'vetried  'Mark all upgrades' [then apply] and tried the 'Reload' options in SPM 

then try                  edit > fix broken packages

If this doesn't work open a terminal and try 

sudo apt-get update 

and /or 

sudo apt-get upgrade.

There are more options to do things like forcebly remove broken packages (if you know what they are) such as sudo dpkg -remove- ******* . 

For more info on all this try

[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)

---

