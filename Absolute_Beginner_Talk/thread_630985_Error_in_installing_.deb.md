---
title: "Error in installing .deb"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by championboxes on 2007-12-03
When I try to install a .deb I get an error message saying "Error: Dependency is not satisfiable: libc6" what should I do to fix this?

---

### Post by TeaSwigger on 2007-12-04
Well that means that a component (a lib, library, think system) isn't the right version to work with that .deb. Sometimes its handy to look up the exact name of the package it's moaning about here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
and see what version you have. Sometimes you can install the version it wants. Sometimes you're better off forgetting it. Or sometimes trying to compile the thing from source will work. Depends on the... dependencies the app needs and what was used on  the system that compiled the .deb of it... er well I'm blabbering at this point but you get the idee ;) You could post the exact app, your version of ubuntu, what it says it wants, and maybe someone can help.

---

### Post by vikramsharma on 2007-12-04
> **championboxes said:**
> When I try to install a .deb I get an error message saying "Error: Dependency is not satisfiable: libc6" what should I do to fix this?

Goto to Synaptic Package Manager and look for libc6 (in most of the cases it's installed) also look for libc6-dev package and install it.  Hope you know where to find Synaptic Package Manager, in case you don't it goto System_>Administration_>Synaptic Package Manager.  Hope this helps you out.

---

### Post by championboxes on 2007-12-04
I searched through the package manager and it said that libc6-dev was installed... well actually I am trying to install a few things... several of them are games... warsow, assaultcube, openarena... I am currently running fiesty (7.04)... I have installed these packages on gusty but i was having too many problems with gusty so i went back to fiesty...

---

### Post by hyper_ch on 2007-12-04
where did you get the debs from? are they built for ubuntu or debian or any debian-based system?

---

### Post by championboxes on 2007-12-04
The deb's i found are [Here]("http://www.getdeb.net")

---

