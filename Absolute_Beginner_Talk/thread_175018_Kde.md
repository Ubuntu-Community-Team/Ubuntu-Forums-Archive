---
title: "Kde"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by rameez on 2006-05-12
Sorry if this is a stupid question, I know kubuntu is available, but can you install KDE on ubuntu? like I am running what I dont want to use gnome, is the only way to do this is to install kubuntu or can I install kde on my computer without a complete system change.

---

### Post by aysiu on 2006-05-12
Paste these two commands into a terminal: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` Log out, select session, KDE, log in. You're in.

---

### Post by rameez on 2006-05-12
```
Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  openoffice.org2-kde
Should I go ahead and install the packages anyway?
To continue, enter "Yes"; to abort, enter "No":

```

Its a quite big system change just wondering if this is a good idea to install it, is it easy to remove if I dont like it later?

---

### Post by richbarna on 2006-05-12
sudo apt-get install kde-desktop
sudo aptitude remove gnome-desktop

---

### Post by Engnome on 2006-05-12
Open ofice is not a problem, if you want to uninstall kde you kan just do 

sudo aptitude remove kubuntu-desktop

It has worked for me, got bored with kde, felt like doing anything took 2-3 more clicks than gnome.

Edit: We posted at the same time.... just so you know you dont have to remove gnome if you dont want to.

---

