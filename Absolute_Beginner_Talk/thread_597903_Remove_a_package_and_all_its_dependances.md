---
title: "Remove a package and all its dependances"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by benton on 2007-10-30
Hi there,

I installed gnome-applets in Xubuntu and along with this package it installed tons of Gnome stuff. Now if I try:

sudo aptitude purge gnome-applets

or 

sudo apt-get remove --purge gnome-applets

I'm offered the option to uninstall gnome-applets only. No mention of the other packages it installed along with it.

So how can I get rid of everything?

Regards,

-Benton

---

### Post by aysiu on 2007-10-30
```
sudo apt-get remove gnome-applets
sudo apt-get autoremove
```

---

