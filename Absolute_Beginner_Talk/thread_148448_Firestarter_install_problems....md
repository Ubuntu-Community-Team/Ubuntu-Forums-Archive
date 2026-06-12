---
title: "Firestarter install problems..."
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by Pelham123 on 2006-03-22
Hi. 

I have been trying to install Firestarter on Ub5.10. I have tried following various tutorials, but am stuck....

- initially tried Automatix, but after 'install' I was left with 2 files, an XML file with 'Applications -> System Tools->Firestarter' text inside. Also a desktop.config file is listed under 'firestarter' file search. No Firestarter entry is listed under Apps, Sys tools. 

- tried apt-get update/apt-get install firestarter, package seems to download but doesn't install?

-tried manual download and install from .tgz file, get to the ./configure stage and had to apt-get libxml & gcc. Now ./configure gives the following error..'C compiler cannot create executables'

I have a feeling that every time I install the needed module, another will take its place. The problem is I don't really know where to go from here, what modules will I need. In Synaptic Package Manager I can see listed the modules/packages that I have, under file search I had gcc listed, so why did I need to apt-get...Confused!

Thanks

---

### Post by alamba on 2006-03-22
what do you get when you execute the following in a terminal window:
./firestarter

---

### Post by Jimmey on 2006-03-22
Yeha, Firestarter installs, just doesn't appear in the applications menu ( until you restart X, I think. ) To run it, type 
> sudo firestarter in a terminal window.

---

### Post by Perfect Storm on 2006-03-22
a
```
killall gnome-panel
```
can do it. No need to restart. 8)

---

### Post by Pelham123 on 2006-03-22
Excellent! Killall gnome-panel did the trick.

Thanks for all your replies.

---

