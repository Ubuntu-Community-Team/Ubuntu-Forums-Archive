---
title: "Graphics Problem"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by joshnz on 2006-09-25
My computer stop responding  when i install drivers for Nvidia 7800GTX i use the programme called Automatix to install the drivers . Can some one plez help me? i have to reinstall ubuntu evry time this happens. :evil:

---

### Post by xyz on 2006-09-25
How about trying to remove them for a start.See what happens.
I think (please check Automatix site on how to remove) the command line is:
```
sudo apt-get remove ndisgtk ndiswrapper-utils network-manager-gnome
```
For KDE, it's different.

---

