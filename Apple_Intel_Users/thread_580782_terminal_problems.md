---
title: "terminal problems"
date: 2007-10-19
forum: Apple Intel Users
---

### Post by alSuhail on 2007-10-19
Hi everyone. I'm using the sticky at the top of this forum to configure the basics for my new installation of gutsy. Every time I try to download a package for installation, I get this message "E: Couldn't find package...". This, for example, when I tried to install synaptics for the trackpad:

sudo apt-get install xserver-xorg-input-synaptics gsynaptics
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-synaptics is already the newest version.
E: Couldn't find package gsynaptics

I get that last line for every package I try. Anyone know what the problem is?

---

### Post by cyberdork33 on 2007-10-19
> **alSuhail said:**
> Hi everyone. I'm using the sticky at the top of this forum to configure the basics for my new installation of gutsy. Every time I try to download a package for installation, I get this message "E: Couldn't find package...". This, for example, when I tried to install synaptics for the trackpad:

sudo apt-get install xserver-xorg-input-synaptics gsynaptics
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-synaptics is already the newest version.
E: Couldn't find package gsynaptics

I get that last line for every package I try. Anyone know what the problem is?Maybe they have removed that package?

try
```
sudo aptitude search gsynaptics
```
maybe they just renamed it.

---

