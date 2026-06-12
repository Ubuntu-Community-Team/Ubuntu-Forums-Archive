---
title: "Get away from my Ubuntu, Kubuntu"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-07-12
I have installed Kubuntu over my Ubuntu installation, so I could give it a try. But I just decided to stay with Ubuntu. So I uninstalled Kubuntu. Atleast thats what I thought, Becouse there are still some Kubuntu stuff left on my computer. Like when I boot up, and get to the loading screen it says Kubuntu, instead of the usual Ubuntu. And there are still some programs left too. I have noticed Konsole, and konquerer is still there. Now how do I get rid of all these?

---

### Post by Sonic Alpha on 2006-07-12
Did you install Kubuntu OVER Ubuntu, or just install the KDE stuff through the package manager?

---

### Post by lapsey on 2006-07-12
synaptic is a bit busy ATM for me to confirm this, but if you open Synaptic and search for "kubuntu-desktop" in dependencies, you should find all the packages that were installed with it.

---

### Post by MrHorus on 2006-07-12
If you have KDE and gnome installed you can select "Sessions" at the login screen and then choose which you want this time and as your default.

---

### Post by lapsey on 2006-07-12
Correction:

Open up synaptic package manager, click on search, type in 'kde' and select 'dependencies' from the menu, and hit search.

Synaptic will list all the packages that depend on other packages with 'kde' in their name. Click on the 'S' column header to sort the items by status and  mark them for removal as you want. 

Some things like tango-icon-theme don't have to depend on KDE so be careful about what you do select for removal: chances are you will only need to select a few of them - synaptic will remove the 'parent' dependencies automatically.

---

### Post by fluffington on 2006-07-12
From [this thread](http://www.ubuntuforums.org/showthread.php?t=212332):
> **aysiu said:**
> You don't need to reinstall.

Just do this:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

and then this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

and next time, use *aptitude* instead of *apt-get* or Synaptic:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

