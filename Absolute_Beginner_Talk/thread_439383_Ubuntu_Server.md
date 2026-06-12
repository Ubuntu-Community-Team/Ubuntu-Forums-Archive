---
title: "Ubuntu Server"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by xstevex on 2007-05-10
I am trying to add a GUI to a ubuntu server install without an internet connection at the moment, is it possible to use the Live CD and tell it to install GNOME/KDE from that without adding any of the extras, i want the server features with a GUI for ease of use.

---

### Post by Nekiruhs on 2007-05-10
not certain about how this would work, but I think you can setup the CD to be a repo and then sudo apt-get install ubuntu-desktop.

---

### Post by Bachstelze on 2007-05-10
What's the use of a server without internet connection ? Anyway, you can use the Ubuntu/Kubuntu/Xubuntu Alternate CD to install the appropriate *ubuntu-desktop package depending on the desktop you want.

---

### Post by annda on 2007-05-10
the server cd does not include a gui. but if you can download the desktop cd on another computer, you can use that.

---

### Post by xstevex on 2007-05-10
@HymnToLife 
I want to ready it for when i get a wireless connection, at the moment only one of my computers has internet. 

@annada, HymnToLife, Nekiruhs:
Thanks for your help, basically, what i wanted to know, was whether or not it would recognise the Desktop CD as a repository or would i have to configure it

---

### Post by Bachstelze on 2007-05-10
Not sure about the Desktop CD but the Alternate CD definitely works as a repository. Just insert it and you will be asked if you want to add it. If for some reason it doesn't prompt you or you want to do it manually, open a temrinal and do

```
sudo apt-cdrom add
```

Then insert your CD if you haven't done it already and press Enter. When apt is done scanning your disc, you can do

```
sudo aptitude install ubuntu-desktop
```

or kubuntu/xubuntu depending on the desktop you want.

---

### Post by xstevex on 2007-05-10
Thank you :)

thats exactly what i needed :D

---

