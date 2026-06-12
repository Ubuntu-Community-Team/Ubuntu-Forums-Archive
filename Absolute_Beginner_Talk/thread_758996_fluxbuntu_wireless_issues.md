---
title: "fluxbuntu wireless issues"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-04-18
I have tried plain old ubuntu with gnome, xfce, and kde on my amd64 desktop with a wireless card.  Usually, when I run the install (I have done a fresh install several times on this machine), the wrong driver is loaded.  This has always be fixed by the following code:

```

echo blacklist prism54 | sudo tee -a /etc/modprobe.d/blacklist
sudo modprobe prism54pci

```

I erased ubuntu with gnome and installed fluxbuntu. I used the same code and the terminal said that it blacklisted the prism54 driver, etc.  In the standard ubuntus, network manager usually detects my networks after that.  However, the network config app in fluxbuntu did not.  Please help.  Don't tell me to post in their forums, I know many of you use or have knowledge of fluxbuntu/fluxbox.  If ubuntu came out with an official version, I would use it.

---

### Post by eriqjaffe on 2008-04-18
I've had success with WICD, although that was in a straight Fluxbox-over-CLI install.  A lot of people swear by Wifi Radar, but I couldn't get it to work with my old 802.11b card.

---

### Post by hikujk123 on 2008-04-18
Can you please give me a detailed response?  I am relatively new to linux.  Also, my only internet connection on that computer is the one that doesn't work.  I'll have to go back to ubuntu if this doesn't work.

---

### Post by hikujk123 on 2008-04-18
Bump!  Maybe I'll switch openSUSE.  I don't know.  I would really like to use fluxbuntu.  All of the standard buntus cause GUI problems on my computer but at least wifi works.

---

### Post by hikujk123 on 2008-04-19
i can see that this will get me nowhere.   I already switched back to xubuntu.  Hopefully I won't have GUI problems if I avoid transparency.

---

