---
title: "restricted issues with 7.1"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by asakurax on 2007-10-19
i just finished installing Ubuntu 7.1(Gutsy right?)
when i try to install the restricted drivers, i get this:

Restricted Drivers Manager cannot be installed on your computer type (i386)
Either the application requires special hardware features or the vendor decided to not support your computer type.

my video card is fx5600

---

### Post by andrewsomething on 2007-10-19
Restricted Drivers Manager should come installed by default.

Look under:  System >> Administration >>  Restricted Drivers Manager.

What are the steps you took to get that error message?

---

### Post by bwallum on 2007-10-19
With that card you should be able to use the nvidia driver, which is an 'accelerated driver'. You don't want the open 'nv' driver if you want all the eye candy.

The nvidia driver is called nvidia-glx-new in Synaptic Package Manager. Search for it and check it is installed. You should then be able to select it with the Restricted Drivers Manager. Both these 'managers' are available from the System>Administration menu.

---

### Post by asakurax on 2007-10-19
well, i went to the driver manager, and tried to enable the driver
then i got an error, it was something like :"nvidia-glx-new" is not enabled
so i uninstalled the restricted package using the "application>>add remove"
and now i cant reinstall it...

edit: all i see in synaptic is "nvidia-kernel-common"
and i need the driver for the refresh rate..
im kinda stucked here with 60 hz refresh rate...

---

### Post by andrewsomething on 2007-10-19
> **asakurax said:**
> well, i went to the driver manager, and tried to enable the driver
then i got an error, it was something like :"nvidia-glx-new" is not enabled
so i uninstalled the restricted package using the "application>>add remove"
and now i cant reinstall it...

edit: all i see in synaptic is "nvidia-kernel-common"
and i need the driver for the refresh rate..
im kinda stucked here with 60 hz refresh rate...

Ahh... You uninstalled it. Try running:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by mikeyphi on 2007-10-19
Have you confirmed that all the repositories are enabled - System/Administration/Software sources

---

### Post by asakurax on 2007-10-19
> **mikeyphi said:**
> Have you confirmed that all the repositories are enabled - System/Administration/Software sources

ha,  i enabled everything and it works fine

thanks (:

---

