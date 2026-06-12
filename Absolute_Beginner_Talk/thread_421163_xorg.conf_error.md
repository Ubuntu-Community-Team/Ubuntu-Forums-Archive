---
title: "xorg.conf error"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2007-04-24
When I try to start Ubuntu it gets all the way to where it would start GDM, but fails.  I get an error message that reads:

> could not open default cursor font "cursor"

How would I go about correcting this error so that GDM loads.

Thanks in advance,

Don

---

### Post by Ziox on 2007-04-24
you can try rebuilding xorg.conf file:

sudo dpkg-reconfigure xserver-xorg

---

### Post by alienexplorers on 2007-04-24
Tried that already with no luck.  Any other ideas?

---

### Post by alienexplorers on 2007-04-24
bump

---

### Post by sisco311 on 2007-04-24
try to install xfonts-base:
```
sudo aptitude install xfonts-base
```

---

### Post by alienexplorers on 2007-04-24
Re-loading the xfonts-base fixed the problem.  Thanks for all your help.

---

