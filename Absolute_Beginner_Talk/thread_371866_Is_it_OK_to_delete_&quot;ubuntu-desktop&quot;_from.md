---
title: "Is it OK to delete &quot;ubuntu-desktop&quot; from Synaptic?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-02-27
Is it OK to delete "ubuntu-desktop" from Synaptic?
I'm trying to go back to square one with my SAMBA installations, so I'm un-installing any kind of SAMBA programs that weren't in Ubuntu from the start.  And I could only remember these 2 samba programs being installed by me trough synaptic.  But doing so made synaptic ask if I'm also want to [COLOR="Red"]un-install ubuntu-desktop[/COLOR], now that doesn't sound sane or does it?
Should I or should I not proceed with this un-installation?
> 
samba-common will be removed
smbclient will be removed
[COLOR="Red"]ubuntu-desktop will be removed[/COLOR]

[IMG]http://i18.tinypic.com/3zlyjnn.png[/IMG]
[http://i18.tinypic.com/3zlyjnn.png](http://i18.tinypic.com/3zlyjnn.png)

---

### Post by tribble222 on 2007-02-27
ubuntu-desktop is gnome and all your desktop programs bundled with ubuntu.  So no, you don't want to remove ubuntu-desktop unless you want to remove gnome.

Edit: nevermind, I'm wrong.  See below for correct information.

---

### Post by christhemonkey on 2007-02-27
It is ok to remove ubuntu-desktop, but ubuntu-desktop meta-package is all the apps that are installed by default. 
So samba-common and smbclient are installed by default.

@tribble222
Removign ubuntu-desktop doesnt remove all its dependencies... So gnome and things wont be removed.
It is just a meta-package.

---

### Post by jingo811 on 2007-02-27
ic tnx for the pointers.  I thought those 2 samba programs were installed manually by me, I guess I can go on testing my plan on making SAMBA work again :)

---

### Post by ComplexNumber on 2007-02-27
> **tribble222 said:**
> ubuntu-desktop is gnome and all your desktop programs bundled with ubuntu.  So no, you don't want to remove ubuntu-desktop unless you want to remove gnome.
thats true, it is a metapackage that has lots of programs bundled  together.....but that only applies when one is installing. it can be safely uninstalled.  a metapackage is simply a container. as an analogy, a metapackage is like a tin of sardines. the tin(metapackage) becomes useless after you have got your sardines and sauce(ie applications).

---

### Post by aysiu on 2007-02-27
I think it's recommended you keep it installed if you're planning to *upgrade* to the next release (instead of doing a fresh *reinstall*).

---

### Post by MkfIbK7a on 2007-02-27
yes what aysiu said...

its just a meta package and will not remove anything else but it is used in the upgrade to upgrade everything else..

---

