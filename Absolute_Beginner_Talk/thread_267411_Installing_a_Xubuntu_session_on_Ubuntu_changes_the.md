---
title: "Installing a Xubuntu session on Ubuntu changes the boot screen."
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2006-09-28
Installing a Xubuntu session on Ubuntu changes the boot screen to the Xubuntu one, I dont want this. How do I change it back?

---

### Post by WalmartSniperLX on 2006-09-28
I had the same problem :-D  does anyone know how to fix this?

---

### Post by Metacarpal on 2006-09-28
Uninstall xubuntu-artwork-usplash
Reinstall usplash

You can do it in Synaptic (System > Administration > Synaptic) or in terminal by:

```
sudo aptitude remove xubuntu-artwork-usplash
sudo aptitude reinstall usplash
```

It'll give you a warning that it will have to remove xubuntu-desktop - don't worry.  xubuntu-desktop is a dummy package only meant to help with the installation of Xubuntu.

However, that being said, if you used aptitude (as opposed to apt-get or synaptic) to install Xubuntu and would like to remove it easily later, removing the xubuntu-desktop package will prevent you from doing so.  You can still [remove it easily]("http://www.psychocats.net/ubuntu/puregnome") if you want to, though.

---

