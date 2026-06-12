---
title: "How Do I back off a driver update"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Skip Da Shu on 2007-11-11
I installed a legacy nvidia driver and now I get no display.

I knew it was going too easy.

I hit ESC at boot and got to a boot menu (GRUB?) and there I select an option that took me into a "recovery mode" or "safe mode" of sorts.  I have a command prompt with "boot" as the user.  

Can somebody walk me thru backing out the Nvidia Legacy driver that caused this?

Thanx, Skip

---

### Post by matthewcraig on 2007-11-11
Gutsy has a bulletproof-X mode that should let you login with VESA video drivers.  Then, you can make your X settings.  Is that working?

Sorry, I don't know anything about the Legacy Driver.  Maybe try the graphics forum for this in-depth question?

---

### Post by Skip Da Shu on 2007-11-11
> **matthewcraig said:**
> Gutsy has a bulletproof-X mode that should let you login with VESA video drivers.  Then, you can make your X settings.  Is that working?

Sorry, I don't know anything about the Legacy Driver.  Maybe try the graphics forum for this in-depth question?

Is "X-mode" what I'm in now from the [ESC] boot menu?

---

### Post by Skip Da Shu on 2007-11-11
from **man apt-get** I found that **/var/cache/apt/archives** has recently processed packages.

In that dir I found **nvidia-glx-legacy_1.0.7185+2.6.224-14.9_amd64.deb**

Can someone tell me the best apt-get command line options to completely remove this from my system?

I'll go back to man apt-get as I'm sure I can come up with something from that... just not sure it'll be completely correct.

Thanx, Skip

---

### Post by carlosjuero on 2007-11-11
> **Skip Da Shu said:**
> from **man apt-get** I found that **/var/cache/apt/archives** has recently processed packages.

In that dir I found **nvidia-glx-legacy_1.0.7185+2.6.224-14.9_amd64.deb**

Can someone tell me the best apt-get command line options to completely remove this from my system?

I'll go back to man apt-get as I'm sure I can come up with something from that... just not sure it'll be completely correct.

Thanx, Skip
```

sudo apt-get remove --purge nvidia-glx-legacy_1.0.7185+2.6.224-14.9_amd64
sudo dpkg-reconfigure -phigh xserver-xorg

```

The first one should remove the legacy nVidia driver from your system, the next line will allow you to reconfigure the X display and choose a new display driver.

---

### Post by Skip Da Shu on 2007-11-11
> **Skip Da Shu said:**
> from **man apt-get** I found that **/var/cache/apt/archives** has recently processed packages.

In that dir I found **nvidia-glx-legacy_1.0.7185+2.6.224-14.9_amd64.deb**

Can someone tell me the best apt-get command line options to completely remove this from my system?

I'll go back to man apt-get as I'm sure I can come up with something from that... just not sure it'll be completely correct.

I'm thinking 

```
apt-get purge nvidia-glx-legacy_1.0.7185+2.6.224-14.9_amd64.deb 

apt-get autoclean
```

---

### Post by Skip Da Shu on 2007-11-12
```
sudo dpkg-reconfigure xserver-xorg
```

Got desktop back on first run thru but only at 800x600@85Hz

Took a few more runs thru before I figured out that even though the CRT supported 1024x768@75Hz, the driver or something didn't want it to run over 70Hz.

Thanx to all who provided input.

---

