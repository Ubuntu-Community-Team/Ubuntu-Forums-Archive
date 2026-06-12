---
title: "modconf and depends"
date: 2005-08-03
forum: Apple PPC Users
---

### Post by open_flax on 2005-08-03
hello 
i wont install modconf but in reposity of dselect i find nothing so i serch in ubuntuforums i find this post:
[http://ubuntuforums.org/archive/index.php/t-8859.html](http://ubuntuforums.org/archive/index.php/t-8859.html)
So can i donwload a package  modeconf.deb but i dont know depends and conflicts where i find ?
thanks

---

### Post by heimo on 2005-08-03
Accrording that thread, it's in "universe", which is a section of Ubuntu repository (collection of packages). But it has to be enabled first. This is how you do it:
[https://wiki.ubuntu.com/UniversePackages](https://wiki.ubuntu.com/UniversePackages)

---

### Post by Ptero-4 on 2005-08-03
[QUOTE=heimo]Accrording that thread, it's in "universe", which is a section of Ubuntu repository (collection of packages). But it has to be enabled first. This is how you do it:
[https://wiki.ubuntu.com/UniversePackages](https://wiki.ubuntu.com/UniversePackages)[/QUOTE]
 And you should use aptitude or synaptic. Dselect is obsolete and no longer supported.

---

### Post by open_flax on 2005-08-04
I add in /etc/apt/sources.lst a reposity of universe but i dont find any package call modconf.

---

### Post by heimo on 2005-08-04
Ok, I went searching and according to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) modconf is only in Breezy (5.10), however the thread you linked talks about Warty (4.10), and you're probably running Hoary (5.04). 

Looks like it doesn't have much dependencies, so it may be possible to install it manually (downloading and using dpkg -i packagename). I can't test it, I'm running Breezy and I can just use apt-get or synaptic to install it (actually just did that, works).
[http://packages.ubuntu.com/breezy/base/modconf](http://packages.ubuntu.com/breezy/base/modconf)

---

