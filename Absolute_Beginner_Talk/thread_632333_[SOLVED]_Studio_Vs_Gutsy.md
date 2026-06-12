---
title: "[SOLVED] Studio Vs Gutsy"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by allsys3 on 2007-12-05
is there a way to install gutsy and then upgrade to studio without losing all the other cool stuff in gutsy?

---

### Post by rsambuca on 2007-12-05
I believe all of the Ubuntu Studio packages are now in the standard Gutsy repositories.  If you open the Synaptic Package Manager (System - Administration - Synaptic Package Manager) and search for 'ubuntustudio', you will find all of the packages.  You can then simply select them for installation.  I am not sure, but you may have to install the low-latency kernel separately.

---

### Post by s.victor on 2007-12-05
Yes, that's what I did :)

You should install only ubuntustudio-desktop if you want the UbuntuStudio "look", and can optionally install ubuntustudio-audio, ubuntustudio-audio-plugins, ubuntustudio-graphics and ubuntustudio-video if you want a complete UbuntuStudio system. It is also recommended to install the linux-rt package. You can do all that from Synaptic.

Then you have to change the theme (System -> Preferences -> Appearance -> Theme) to UbuntuStudio, and the login window (System -> Administration -> Login Window -> Local) to Ubuntu-Studio v2.

---

### Post by allsys3 on 2007-12-12
Im not to concerned about the themes but its mainly all the audio programs im looking for so thanks alot

---

