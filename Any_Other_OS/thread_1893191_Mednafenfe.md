---
title: "Mednafenfe"
date: 2011-12-06
forum: Any Other OS
---

### Post by dagoss on 2011-12-06
I recently downloaded the deb and installed it (on Linux Mint 12) and I am getting the error "ImportError: No module named mfe" from command line. I checked in the python directories in /usr/lib/ and the mfe folder is in the folders for python2.4, 2.5, and 2.6, but not 2.7 which seems to be the version of python run from the python command. Could this be causing this issue or is there some command that needs to be run to tell python to update its list of available modules or something.

---

### Post by wwwookie on 2011-12-09
Hi Dagoss,

I got exactly the same problem. Modules for python 2.4, 2.5, 2.6 but not 2.7.
My original thought was to run an older version of python, but 2.6 has been dropped in Natty.
My workround is just to copy the python2.6 module into the 2.7 directory.

```
sudo cp -r /usr/lib/python2.6/dist-packages/mfe/ /usr/lib/python2.7/dist-packages/
```

Python 2.7 seems to be backward compatible enough to handle this.

---

### Post by Perfect Storm on 2011-12-09
Split from old thread and moved to Other OS/Distro Talk.

---

### Post by Sarteck on 2012-06-17
> **wwwookie said:**
> Hi Dagoss,

I got exactly the same problem. Modules for python 2.4, 2.5, 2.6 but not 2.7.
My original thought was to run an older version of python, but 2.6 has been dropped in Natty.
My workround is just to copy the python2.6 module into the 2.7 directory.

```
sudo cp -r /usr/lib/python2.6/dist-packages/mfe/ /usr/lib/python2.7/dist-packages/
```

Python 2.7 seems to be backward compatible enough to handle this.

AMG, THANK YOU, WWWOOKIE!  :3

I've been trying to get the front end to work, and this workaround works perfectly for me.

---

