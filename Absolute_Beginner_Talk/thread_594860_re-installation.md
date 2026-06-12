---
title: "re-installation"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by liquidus219 on 2007-10-28
I have an Acer 5600 series laptop dual-booting WInXP and Kubuntu.

I want to install pure Ubuntu over Kubuntu, so I wanted to just install over the Kubuntu partition. Is this possible, or will it mess up my grub?

---

### Post by Pumalite on 2007-10-28
You can install over Kubuntu. Make sure you point to the right partition. Go Manual. Your Grub will be replaced by a brand new one that will also recognize Windows.

---

### Post by seshomaru samma on 2007-10-28
it will not mess up your grub
however you can just install gnome on top of kubuntu, it will be much easier and much safer
```
sudo aptitude install ubuntu-desktop
```

---

### Post by lpevey on 2007-10-28
If you want to switch to kde instead of gnome, you can do that without re-installing everything.  You can just type:

sudo apt-get install kubuntu-desktop

I believe this will even update your system to show the kubuntu splash at startup.

---

