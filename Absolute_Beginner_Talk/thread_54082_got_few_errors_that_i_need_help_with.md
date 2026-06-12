---
title: "got few errors that i need help with"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by aran384 on 2005-08-03
First one is that i installed zope to see what it was and couldnt work out how the ****  to use it so i uninstalled it (well i think i did) 

and now on bootup i get error cos it trys to load zope.....??

Second is when i try to install something with sudo apt-get install

mine now getting this error to do with zope ??  :-?  :-?

---

### Post by aran384 on 2005-08-03
ive got a paste of the error god no's what it means =/ 

Setting up zope (2.6.4-1.6ubuntu1) ...
Setting up initial user for default... done.
Initializing Zope instance home for default... failed: getgrnam(): name not foun d
default: init: getgrnam(): name not found
dpkg: error processing zope (--configure):
 subprocess post-installation script returned error exit status 2
Setting up xlibmesa-glu-dev (6.8.2-10) ...
Setting up libqt3-mt-dev (3.3.3-7ubuntu3) ...
Errors were encountered while processing:
 zope
'getpwnam(): name not found: zope'
use `dzhandle help' for help on actions and arguments

E: Problem executing scripts DPkg::Post-Invoke 'dzhandle restart-pending-instanc es'
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by KingBahamut on 2005-08-03
[QUOTE=aran384]ive got a paste of the error god no's what it means =/ 

Setting up zope (2.6.4-1.6ubuntu1) ...
Setting up initial user for default... done.
Initializing Zope instance home for default... failed: getgrnam(): name not foun d
default: init: getgrnam(): name not found
dpkg: error processing zope (--configure):
 subprocess post-installation script returned error exit status 2
Setting up xlibmesa-glu-dev (6.8.2-10) ...
Setting up libqt3-mt-dev (3.3.3-7ubuntu3) ...
Errors were encountered while processing:
 zope
'getpwnam(): name not found: zope'
use `dzhandle help' for help on actions and arguments

E: Problem executing scripts DPkg::Post-Invoke 'dzhandle restart-pending-instanc es'
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (1)[/QUOTE]
 apt-get remove zope ? 

or attempt to remove via Synaptic?

---

