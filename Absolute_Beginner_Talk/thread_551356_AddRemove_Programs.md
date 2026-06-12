---
title: "Add/Remove Programs"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by NEUR0M4NCER on 2007-09-15
Hi all. When I try to run Add/Remove Programs, it hangs halfway through loading. I've tried in a terminal, and here's what I get:

** (gnome-app-install:6062): WARNING **: return value of custom widget handler was not a GtkWidget
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 315, in <module>
    sys.argv, as, transient_for, addon_cd)
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 262, in __init__
    self.updateCache(filter_to_restore)
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 987, in updateCache
    activation_style=self.activation_style)
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 123, in __init__
    self.refresh(progress)
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 311, in refresh
    self.initListStores(item, self)
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 379, in initListStores
    category.applications = gtk.TreeModelSort(category.filtered_applications)
SystemError: ../Python/getargs.c:1270: bad argument to internal function


I've looked through similar threads, but can't find a solution; any help would be great.


Regards

---

### Post by cvaty on 2007-09-15
apt-get

man apt-get

```

sudo apt-get update
sudo apt-get upgrade

```

?

---

### Post by Polemistis on 2007-09-15
> **NEUR0M4NCER said:**
> Hi all. When I try to run Add/Remove Programs, it hangs halfway through loading. I've tried in a terminal, and here's what I get:

** (gnome-app-install:6062): WARNING **: return value of custom widget handler was not a GtkWidget
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 315, in <module>
    sys.argv, as, transient_for, addon_cd)
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 262, in __init__
    self.updateCache(filter_to_restore)
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 987, in updateCache
    activation_style=self.activation_style)
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 123, in __init__
    self.refresh(progress)
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 311, in refresh
    self.initListStores(item, self)
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 379, in initListStores
    category.applications = gtk.TreeModelSort(category.filtered_applications)
SystemError: ../Python/getargs.c:1270: bad argument to internal function


I've looked through similar threads, but can't find a solution; any help would be great.


Regards


maybe your sources.list file is corrupt?
Check the /etc/apt/sources.list file.

Also try what the guy above said about update.

---

### Post by NEUR0M4NCER on 2007-09-15
Hiya - thanks for the reply. I really am new to Linux, so it even took me a while to realise I needed to use gedit to open the sources list... now what would I be looking for if something there's corrupt? Cheers

---

### Post by alienexplorers on 2007-09-15
If you ran sudo apt-get update and sudo apt-get upgrade then the source list should be OK if you did not get any errors.

---

### Post by NEUR0M4NCER on 2007-09-16
KK. So no errors there. Any other ideas as to what might be causing my problem?

---

### Post by NEUR0M4NCER on 2007-09-16
... also. There is something that might be causing an issue on the sources.list from automatix - it never manages to connect on apt-get update. When I try to remove the reference to it in the list i'm told it's read only. How do I get 'admin priveleges' or whatever.


Thanks

---

### Post by meierfra on 2007-09-16
To run a program as root you need to use "sudo"

:```
sudo gedit /etc/apt/sources.list  
```

---

### Post by NEUR0M4NCER on 2007-09-16
Lovely - thanks. I'll see if that makes any difference. Still no luck with Add/Remove Programs though.

---

### Post by NEUR0M4NCER on 2007-09-16
If it's any help, the bar gets as far as 'Loading Applications', then dies. Here's what I get when I run gnome-app-install in a terminal:

** (gnome-app-install:12487): WARNING **: return value of custom widget handler was not a GtkWidget
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 315, in <module>
    sys.argv, as, transient_for, addon_cd)
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 262, in __init__
    self.updateCache(filter_to_restore)
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 987, in updateCache
    activation_style=self.activation_style)
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 123, in __init__
    self.refresh(progress)
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 311, in refresh
    self.initListStores(item, self)
  File "/usr/lib/python2.5/site-packages/AppInstall/Menu.py", line 379, in initListStores
    category.applications = gtk.TreeModelSort(category.filtered_applications)
SystemError: ../Python/getargs.c:1270: bad argument to internal function

---

