---
title: "Planner Backport problem"
date: 2005-08-24
forum: Bug Reports / Support
---

### Post by AndyAWS on 2005-08-24
I got the following error when trying to update Planner 0.13-0.4 (From Gnome Office) from the Backports.


```
The following packages have unmet dependencies:
  planner: Depends: libgda2-3 but it is not going to be installed
E: Broken packages
```
Attempting to install libgda2-3 causes glade-gnome-2, gnome-devel, libgda2-1, libgnomedb2-3 and libgnomedb2-common, to want to be removed.

---

