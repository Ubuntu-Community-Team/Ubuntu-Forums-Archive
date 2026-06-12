---
title: "how to install unity in linuxmint 14"
date: 2013-01-10
forum: Any Other OS
---

### Post by MMALLOW on 2013-01-10
hi happy new year

how to install unity in linuxmint 14 Cinnamon

thanks

---

### Post by zombifier25 on 2013-01-10
Linux Mint is based on Ubuntu, so Unity is just one apt-get away.
```
sudo apt-get install unity
```
Then log out and choose the session "Ubuntu".

---

### Post by haqking on 2013-01-10
it should also be in the software centre

[http://www.linuxbsdos.com/2011/12/11/how-to-run-unity-desktop-on-linux-mint-12/](http://www.linuxbsdos.com/2011/12/11/how-to-run-unity-desktop-on-linux-mint-12/)

---

### Post by MMALLOW on 2013-01-10
thanks 
still not work

---

### Post by Frogs Hair on 2013-01-10
Keep in mind Unity 3D is a Compiz plug-in and don't know if mint 14 has it installed . To use the Unity settings you will need the CCSM.

---

### Post by howefield on 2013-01-10
Thread moved to the "*Other OS/Distro Talk*" forum.

---

### Post by MG&amp;TL on 2013-01-10
> **MMALLOW said:**
> thanks 
still not work

Obvious question: why not use Ubuntu?
Obvious question 2.0: have you logged out and selected the Unity session?

---

### Post by xenopeek on 2013-01-10
To install Unity on Linux Mint, at the very least you will need to to install:
- unity
- gnome-session

Without the latter (which you didn't yet install I think), you won't be able to run Unity. You may also need to replace mdm (Linux Mint's login screen) with lightdm or gdm. But perhaps not, so give it a go without first.

You can get the full Ubuntu experience on Linux Mint by installing the meta-package "ubuntu-desktop" that installs the complete Unity desktop including all its included default programs and add-ons.

---

### Post by BBQdave on 2013-01-11
> **MG&TL said:**
> Obvious question: why not use Ubuntu?

+1

Ubuntu 12.10 is what ya need, don't take the long path, go straight to it :D

---

### Post by zombifier25 on 2013-01-11
> **BBQdave said:**
> +1

Ubuntu 12.10 is what ya need, don't take the long path, go straight to it :D

And if you need the Linux Mint goodness you can install their PPAs.

---

