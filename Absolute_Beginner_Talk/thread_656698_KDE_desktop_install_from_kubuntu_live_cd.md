---
title: "KDE desktop install from kubuntu live cd"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2008-01-02
Hey there i have ubuntu 7.10(gnome DE) installed on my pc, but i want to be able to use the KDE DE as well, i have no internet connection on my home pc, so was wondering if its possible to install the kubuntu DE onto my pc via the kubuntu 7.10 live cd?

---

### Post by sumguy231 on 2008-01-02
As a matter of fact you can, run
```
sudo apt-cdrom add
```
from the command line, and insert the disc when it asks you to.
Then do:
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```
When it's done, KDE will be installed.

---

### Post by dynamethod on 2008-01-02
Excellent, thanks very much!

---

### Post by dynamethod on 2008-01-02
actually it didnt work out :S

what had happend is when i ran sudo apt-get update, it tried to fetch updates from the internet, which i dont have with my home pc

so i unselected all the repositories that need a net connection, but when i ran sudo apt-get install kubuntu-desktop it told me that it couldnt find the package :s

---

### Post by aysiu on 2008-01-02
The *kubuntu-desktop* package is not on the live CD. You need the Alternate CD.

---

### Post by dynamethod on 2008-01-02
ah ok, is the Alternate CD available from shipit?, i can only see the live CD's

---

### Post by sumguy231 on 2008-01-03
> **aysiu said:**
> The *kubuntu-desktop* package is not on the live CD. You need the Alternate CD.

Seriously? Why would it not be on the Kubuntu Live/Desktop CD? And wouldn't installing the kde metapackage be a better solution than getting the alternate CD? I guess being forums staff you're probably right, but I could have sworn that all of the Kubuntu base packages would have been contained on the Desktop CD.

Edit: Oh, and as far as I know, you can only get the Desktop CD from Shipit, not the Alternate Install CD.

---

