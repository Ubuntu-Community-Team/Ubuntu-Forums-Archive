---
title: "Switching to AHCI hard drive"
date: 2012-01-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Jeff Root on 2012-01-21
I have an ASUS P5Q-E motherboard and three Western Digital
SATA drives, WD6401AALS.
 
When I set the computer up I left the BIOS setting for SATA
Configuration at the default, "IDE".  After a couple of years
of use, I want to change it to either "AHCI" or maybe "RAID".
 
One of the drives has never been installed, one contains my
data, and the third I am about to repartition and format
before clean reinstal of operating systems.
 
What do I need to know about enabling AHCI mode under Ubuntu
64-bit Maverick Meerkat and 32-bit Karmic Koala?
 
   -- Jeff, in Minneapolis
 
.

---

### Post by kurt18947 on 2012-01-21
I switched between native IDE and AHCI a few times when switching between WinXP & Ubuntu.  My experience was smooth, there was nothing to change beyond the BIOS setting.

---

### Post by varunendra on 2012-01-21
In Linux (any distro), the transition will be smooth as *kurt18947* mentioned.

In win7/Vista, you will have to install additional drivers for ahci (before switching to ahci mode in BIOS).

In XP, you'll have to reinstall XP with ahci enabled in BIOS (or fallback to IDE everytime you wish to switch to XP).

Hope that's all you wanted to know.

As a side note, even though both Maverick and Karmik will pick up the change quite smoothly, you should consider upgrading Karmik to at least 10.04 as it is no more supported now.

---

