---
title: "[SOLVED] pakage install problem"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Modified.Reality on 2008-02-17
I am trying to install a package and keep getting the following message:

Only one software management tool 
allowed to run at the same time.

but I have nothing else running. I even rebooted my computer.

---

### Post by Flyingjester on 2008-02-17
do you have your update manager open along with anything else? add/remove? synaptic?

---

### Post by spiderbatdad on 2008-02-17
try running ```
sudo dpkg --configure -a
``` maybe a package has not completed installation, and has the package management utility tied up.

---

### Post by Modified.Reality on 2008-02-17
Thanks, That code worked perfect. :guitar:

---

