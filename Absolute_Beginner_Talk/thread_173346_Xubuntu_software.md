---
title: "Xubuntu software"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by Reggaeton King on 2006-05-10
Is it possible to install Anjuta IDE on Xubuntu. Can I install any other software or I have limited amount b/c my UI is XFCE?

---

### Post by oscar on 2006-05-10
Yes it should be possible to install it, the desktop environment you use shouldn't matter

---

### Post by Borniet on 2006-05-10
You are never limited by the desktop environment that you use, if you install the libraries of the other environments (KDE or Gnome most probably).

---

### Post by Reggaeton King on 2006-05-10
Thanks

---

### Post by Borniet on 2006-05-10
Thou areth welcome my friend.

---

### Post by az on 2006-05-10
[QUOTE=Reggaeton King]Can I install any other software or I have limited amount b/c my UI is XFCE?[/QUOTE]

The package manager will resolve any dependencies and install the needed kde or gnome libraries.  

When you start something that,for example, depends on KDE libraries from another desktop environment like XFCE, it will run, but it will load the neccessary libs into memory first and may take up a little bit more of your ressources than if it were running in a kde environment - but maybe not since it will not need *all* of kde to run, just some shared libraries (YMMV).   

But it will run fine.

---

