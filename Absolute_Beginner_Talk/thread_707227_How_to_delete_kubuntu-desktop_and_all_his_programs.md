---
title: "How to delete kubuntu-desktop and all his programs"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Fixman on 2008-02-25
Some time ago, I tried kubuntu by installing kubuntu-desktop. As usual, many KDE modules and programs where installed. Is there a way to uninstall then all (kubuntu-desktop+modules+programs)?

---

### Post by overdrank on 2008-02-25
> **Fixman said:**
> Some time ago, I tried kubuntu by installing kubuntu-desktop. As usual, many KDE modules and programs where installed. Is there a way to uninstall then all (kubuntu-desktop+modules+programs)?

Hi and this link can help
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by philinux on 2008-02-25
click the psychocats link below then scroll down to the KDE Gnome links.

---

### Post by justleen on 2008-02-25
i did that once.. its hard to get rid of everything..

One thing you can do: open up /var/log/apt/term.log
find the entry where you installed kubuntu-desktop. It will list all the files it installed for this packages.
from there its a bit of a hassle, but open a terminal, type " sudo apt-get remove " and copy all the package names after it..

---

### Post by bbqsandwich on 2008-02-25
Depending on how much you have customized your system since you installed Ubuntu, you could also simply do a fresh install.

I installed kubuntu-desktop, greenos-desktop and xubuntu-desktop... got tired of them and couldn't totally get rid of everything so I just installed Ubuntu again from scratch. It just seemed easier that way.

---

