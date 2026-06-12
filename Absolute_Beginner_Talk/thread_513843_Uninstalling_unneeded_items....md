---
title: "Uninstalling unneeded items..."
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Bwangster12 on 2007-07-31
I am relatively new to using Linux distros... I've tried a few different ones so far.  I installed a Xubuntu command line system and put a few things I need on it.  It seems to be running much better on my old laptop that some distros I've tried.

When I try to uninstall certain things in Synaptic that were put on somehow by default I get a message saying that Xorg, or Xubuntu-Desktop or Automatix needs to be uninstalled also.  Is there no way of uninstalling the Xclipboard, for example... without uninstalling important stuff?

---

### Post by bren on 2007-07-31
try

sudo apt-get remove

to purge old apps and dependencies

bren

---

### Post by Bwangster12 on 2007-07-31
Using this will let me uninstall something like xcalc without uninstalling EVERYTHING, lol?

---

### Post by dondad on 2007-07-31
> **Bwangster12 said:**
> I am relatively new to using Linux distros... I've tried a few different ones so far.  I installed a Xubuntu command line system and put a few things I need on it.  It seems to be running much better on my old laptop that some distros I've tried.

When I try to uninstall certain things in Synaptic that were put on somehow by default I get a message saying that Xorg, or Xubuntu-Desktop or Automatix needs to be uninstalled also.  Is there no way of uninstalling the Xclipboard, for example... without uninstalling important stuff?
You can let it uninstall the desktop with no problems. After it is done, you can reinstall it with apt-get. The desktop is just a wrapper application, not your actual desktop.

---

### Post by ramjet_1953 on 2007-07-31
One thing you need to be careful of when uninstalling what may appear to be worthless to you is that some packages are what are called meta packages and you may uninstall something that takes a whole lot of other packages with it.

Regards,
Roger :cool:

---

