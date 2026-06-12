---
title: "Install Apps from CD"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by john.n on 2007-01-12
I'v been having a few problems with the net(wont work), but i'v a Linux Format mag with software on it, when i try to install it from that big list(new to Linux.. :D )seems to be trying to connect to download them, but i think there meant to be on the disc. Anyway you can control where Ubuntu searches for software?

---

### Post by orb9220 on 2007-01-12
In synaptic there is an add cdrom to tell it to look there.

But be aware that ubuntu uses .deb files for installation and not .rpm's
You must browse the cd to see how the apps are packaged.

If they end with .deb you can just right-click and open with the gDebi package installer will install the app for you. But you may run into problems.

---

### Post by taurus on 2007-01-12
Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
```

---

