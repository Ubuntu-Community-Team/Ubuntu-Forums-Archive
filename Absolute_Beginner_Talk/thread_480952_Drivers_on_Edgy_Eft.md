---
title: "Drivers on Edgy Eft?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2007-06-22
ne ideas on this ive tried everything i used automatix which i had to reinstall edgy eft, cause i upgraded from hoary, but neways any ideas?

---

### Post by NeoLithium on 2007-06-22
Hiya,
What kind of drivers were you looking for? Graphics Card, Modem...?  There's usually a good list of stuff at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) for video drivers, depending on what one it might be, should that be the case.

---

### Post by Crafty Kisses on 2007-06-22
> **LiNuXxToOthEMaX said:**
> ne ideas on this ive tried everything i used automatix which i had to reinstall edgy eft, cause i upgraded from hoary, but neways any ideas?

Hello again,

First you should go into your package manager and search for "nvidia" depending on your video card you have the option of "nvidia-glx-legacy" or 
otherwise "nvidia-glx". So install the appropiate driver for your video card, just for the record the legacy drivers are for older video cards, but after you have installed your proper drivers from the "package manager" you want to go into your terminal and type the following:

```
sudo nvidia-xconfig
```
Then you should reboot your computer and there ya go, they should be up and running, enjoy.

---

