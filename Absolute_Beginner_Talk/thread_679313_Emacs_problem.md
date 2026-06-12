---
title: "Emacs problem"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by tweikiang on 2008-01-26
> emacs-install: /usr/lib/emacsen-common/packages/install/jde emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 10.
dpkg: error processing emacs21 (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs:
emacs depends on emacs22-gtk | emacs22 | emacs22-nox; however:
  Package emacs22-gtk is not installed.
  Package emacs22 is not configured yet.
  Package emacs22-nox is not installed.
dpkg: error processing emacs (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acl2-emacs:
acl2-emacs depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs which provides emacsen is not configured yet.
  Package emacs22 which provides emacsen is not configured yet.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing acl2-emacs (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eieio:
eieio depends on emacs22 | emacsen; however:
  Package emacs22 is not configured yet.
  Package emacsen is not installed.
  Package emacs which provides emacsen is not configured yet.
  Package emacs22 which provides emacsen is not configured yet.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing eieio (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jde:
jde depends on eieio (>= 1:1.0pre3-6); however:
  Package eieio is not configured yet.
jde depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs which provides emacsen is not configured yet.
  Package emacs22 which provides emacsen is not configured yet.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing jde (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cedet-common:
cedet-common depends on emacs22 | emacsen; however:
  Package emacs22 is not configured yet.
  Package emacsen is not installed.
  Package emacs which provides emacsen is not configured yet.
  Package emacs22 which provides emacsen is not configured yet.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
speedbar depends on cedet-common (>> 1:1.0pre4-1); however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
emacs22
emacs21
emacs
acl2-emacs
eieio
jde
cedet-common
speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)

did any1 know how to solve this???
everytimes i wan to update my ubuntu, sure hav these problem....

---

### Post by HereInOz on 2008-01-26
Are you trying to install this using a deb file, or are you using synaptic package manager?

---

### Post by tweikiang on 2008-01-26
i install by 
sudo apt-get install update

---

### Post by taurus on 2008-01-26
> **tweikiang said:**
> i install by 
**[COLOR="Blue"]sudo apt-get install update[/COLOR]**

:confused:

---

### Post by HereInOz on 2008-01-26
If you have a look in Synaptic, and mark Emacs for installation, you will note that it advises that it will also install all of the stuff that your error message says that you need.

Give Synaptic a try for installing Emacs and it will probably pull together all of the dependencies you need.

---

