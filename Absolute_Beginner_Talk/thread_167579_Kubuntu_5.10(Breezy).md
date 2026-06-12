---
title: "Kubuntu 5.10(Breezy)"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Sonic132 on 2006-04-28
Ok, I posted a thread on the Kubuntu forum but no one resonded so...

I'm downloading it now, and I was wondering if it installs like Ubuntu does, or if it instead installs as a mod/addon/plugin to Ubuntu.

Anyone?

---

### Post by Jagot on 2006-04-28
It installs just like Ubuntu does - no mod/addon/plugin to Ubuntu.

That is, if you are installing from CD.  Obviously you can install the Kubuntu desktop from Ubuntu and vice-versa, in which case you'd be installing it on top of whatever you already have.

---

### Post by Sonic132 on 2006-04-28
Ok...so once I burn it to a CD. 
I just have to install it over Ubuntu and I still keep all my settings and programs?

---

### Post by Jagot on 2006-04-28
Nope.

If you install Kubuntu over your Ubuntu partition then all your settings and programs will be gone, unless you set up a separate /home partition.

You will need to backup everything.

If you want all your settings saved then you may want to install Kubuntu from Ubuntu, so you'll have access to both KDE and Gnome:

```
sudo aptitude install kubuntu-desktop
```

---

### Post by Qrk on 2006-04-28
No

If you want to install kubuntu and keep all of your settings and programs, you don't want to install kubuntu instead of Ubuntu by going through the installation.

Instead, just install kubuntu-desktop in addition to ubuntu. You don't need a cd for this. 

```
sudo aptitude install kubuntu-desktop
```

This will allow you to switch between KDE and Gnome, keeping your installed programs intact. You can use the CD your downloading as a source for this if you'd like (say, if you don't have an internet connection.)

You shouldn't think of Kubuntu as separate from ubuntu, rather as a package that can be added to ubuntu-base.

---

### Post by Sonic132 on 2006-04-28
Thanks. 
I didn't realize I could do that. I got over half the Install CD for it already and then I find out there's an easier way.
LOL.

---

