---
title: "Updating Klamav"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by nikef on 2007-09-09
I am trying to update Klamav
but keep getting this error in the log file

configure: error: Can't find X libraries. Please check your installation and add the correct paths!
***** Return value 1

---

### Post by nikef on 2007-09-09
i am using the kubuntu desktop,is there something i am missing

---

### Post by p_quarles on 2007-09-09
As I'm sure you know, you don't actually need a virus scanner for Linux, since there are known viruses in the wild, and Klamav can't scan for viruses that it doesn't know about.

In any case, it probably needs to be run as root. Hit alt-F2 and type
```
kdesu klamav
```
I use Gnome, so I don't know exactly how the KDE menu editor works, but you should be able to edit the menu entry to include "kdesu," and that will allow you to automatically run it this way from the menu.

---

### Post by nikef on 2007-09-10
thanks

it does not seem to work,i need to update klamav,also i have three programs of klamav start up,when pc first switch on,they all update and scan at the same time,i have tried to quit,but they will not go

---

### Post by nikef on 2007-10-15
Does any1 know how to update klamav x libraries  please
also i only want 1 running thanks.:confused:

---

