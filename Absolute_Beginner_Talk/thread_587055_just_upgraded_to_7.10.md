---
title: "just upgraded to 7.10"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by ac1240 on 2007-10-22
and i dont know where to made compiz work 
how can i do that ?
and theres a way to use kde +compiz ?
and why cant i see the nfts drivers (i have read that 7.10 have that by default)

---

### Post by celettu on 2007-10-22
Compiz should be enabled by default, unless your graphics card isn't up to it or needs a restricted driver, then you have to install that first.

You can try to turn it on in System > Preferences > Appearance.

As for "seeing" the ntfs drivers, what do you mean? If there's a ntfs partition on your HD, just try to access it. It should work.

---

### Post by af20001 on 2007-10-22
Hi,

Assuming your graphics card is compatible, then to activate Compiz select the menu item System>Preferences>Appearance. 

In the dialog that pops up, select the last tab, Visual Effects. From there, you can turn on/off the visual effects. By default, there are only a couple of effects built in. To manage the plugins more effectively, you need to install compiz settings manager through Synaptic. Select the menu item System>Administration>Synaptic Package Manager, enter your password, then do a search for compiz. You need to look for a settings manager option to install.

Hope this helps.

---

### Post by Maestro23 on 2007-10-22
Install NTFS-config to be able to write to your NTFS partition.

> sudo apt-get install ntfs-config

---

