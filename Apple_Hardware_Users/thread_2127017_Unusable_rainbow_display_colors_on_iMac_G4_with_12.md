---
title: "Unusable rainbow display colors on iMac G4 with 12.10"
date: 2013-03-18
forum: Apple Hardware Users
---

### Post by Brian Kendig on 2013-03-18
I have an iMac G4 (700MHz, 1GB RAM, 1024x768 GeForce2 MX) on which I'm trying to install Lubuntu 12.10. When I boot with the default options ("quiet splash"), the screen looks like it's slowly icing over - it's a neat effect but it's not useful; it looks like there's no video driver so it's just discharging a capacitor or something. When I boot with "nomodeset", I get rainbow-colored graphics which are completely unusable - [https://wiki.ubuntu.com/PowerPCKnownIssues#A12.10_Quantal_Quetzal](https://wiki.ubuntu.com/PowerPCKnownIssues#A12.10_Quantal_Quetzal) says that I have to increase the color depth.

I have no idea how to increase the color depth. All the guides I've seen tell me to edit /etc/X11/xorg.conf, but there is no such file on my new 12.10 install. I have files in /usr/share/X11/xorg.conf.d, but none of them mention any screen configuration. I tried setting up the display by creating my own file there, and also at /etc/X11/xorg.conf, but none of it has any effect. I've tried different screen buffers (nouveau, nv, fbdev) and none of them have any effect either.

"lspci" says this about the display: 0000:00:10.0 VGA compatible controller: NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

How do I get Lubuntu 12.10 to display properly on this iMac G4? I'm not trying anything fancy - if anyone else has gotten it to work on this model of Mac, then I should be able as well! Thank you for your help!

---

