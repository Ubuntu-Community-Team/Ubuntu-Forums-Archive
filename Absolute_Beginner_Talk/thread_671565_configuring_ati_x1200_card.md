---
title: "configuring ati x1200 card"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by mrxtambourineman on 2008-01-18
I have a couple of simple questions. First, some background. I have Gutsy 32 bit installed on my laptop. I have enabled the restricted drivers for my card (fglrx).

1. I want to configure my 3d performance and adjust brightness, gamma etc... is there an easy way to do this? I have tried the command "sudo aticonfig --initial" and all I get is: "Found fglrx primary device section
Nothing to do, terminating."

*** The only way I found out to do this was to install the fglrx-control, but its quite lacking in features

2. How do enable "composite" (if I even can for my card) so I can use some of the slick effects of GNOME?

Thank you for your consideration.

*** Had to install the glx-server to get it to work.

---

### Post by spiderbatdad on 2008-01-18
you can enable compiz by installing the package compizconfig-settings-manager from synaptic. then select custom under the visual effects tab in preferences>>appearance.
there is a wiki for tweaking and or installing the appropriate driver to use fglrx...and some tweaks:[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by jleaker01z on 2008-01-18
For some of the slick effects, you can simply go to System>Preferences>Desktop effects.  You dont really have to download and install anything extra unless you just want everything Compiz or Beryl provides.

---

### Post by mrxtambourineman on 2008-01-19
Thanks a lot guys.

---

### Post by intel on 2008-01-19
If you need more help with ATI Radeon X1200 series card visit the support group at

https://groups.google.com/group/x1250/

---

