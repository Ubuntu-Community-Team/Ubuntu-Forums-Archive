---
title: "Install error"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by rannasjem on 2007-02-03
I get the following error when installing updates or anything off of add/remove programs.

graphiviz-cairo subprocess post-installation script returned error on exit    status 127

what is this?

---

### Post by riven0 on 2007-02-03
The first thing I would do is go to synaptic: System >> Administration >> Synaptic Package Manager. Then go to Custom Filters and remove any broken packages. If that still doesn't work, go to the terminal and force the installation:

> sudo apt-get -f install graphiviz-cairo

---

### Post by rannasjem on 2007-02-05
Thanks for the help.  I didn't have any broken packages to uninstall so I went to the terminal to do the force install and got the following message.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package graphiviz-cairo

any ideas?

---

### Post by shareMenaPeace on 2007-02-05
You need to reinstall cairo

[http://www.ubuntuforums.org/showthread.php?t=290534](http://www.ubuntuforums.org/showthread.php?t=290534)

[http://www.google.de/search?hl=de&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=graphviz-cairo+subprocess+&spell=1](http://www.google.de/search?hl=de&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=graphviz-cairo+subprocess+&spell=1)

---

