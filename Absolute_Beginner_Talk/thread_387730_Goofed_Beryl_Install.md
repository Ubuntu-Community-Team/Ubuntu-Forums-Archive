---
title: "Goofed Beryl Install"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by evandec on 2007-03-18
Well I tried to install beryl and royally screwed up my x server configuration file, part of this was due to my aggressive tinkering. Now x wont even boot. 

Is it possible to totally uninstall and reinstall x server? Could I just reset it to its default settings?

---

### Post by annda on 2007-03-18
if you do not a have a back-up xorg.conf (always a good idea to back up important files before you modify them), do this:

sudo dpkg-reconfigure -phigh xserver-xorg

it will help you reset the settings.

---

### Post by Kobalt on 2007-03-18
> **annda said:**
> if you do not a have a back-up xorg.conf (always a good idea to back up important files before you modify them), do this:

sudo dpkg-reconfigure -phigh xserver-xorg

it will help you reset the settings.
This command will only reset the resolution settings, if it's the drivers that are screwed you will need this one to set them up properly again : 
```
sudo dpkg-reconfigure xserver-xorg
```

---

