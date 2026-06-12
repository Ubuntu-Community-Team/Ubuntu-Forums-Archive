---
title: "KDE app in Gnome - $ to £"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by getaboat on 2007-12-15
Eqonomize looks like the persolnal finance app I'll go with, Homebank is preferred but the repo version is buggy and 3.5 - which has the bugs fixed won't run on Feisty. However Eqonomize is a KDE app and I'm running Gnome. How can I change the $ sign to £ used in Eqonomize  in Gnome? It looks like in KDE it is done through a KDE regional setting? Thanks

---

### Post by benerivo on 2007-12-15
I think you could install kcontrol, which is the kde settings manager and should alter kde apps when they are run in Gnome. So```
sudo apt-get install kcontrol
```then```
kcontrol
```when it's installed. Amongst the options is a 'regional / locale' section.

---

### Post by getaboat on 2007-12-16
Thank you that did the trick!

---

