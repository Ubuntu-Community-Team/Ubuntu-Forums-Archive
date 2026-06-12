---
title: "NVIDIA Graphics Card Drivers - no Xorg"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by tprzepiorka on 2007-08-21
Hello,
I finally got my graphics card working after switching from ATI to NVIDIA. Since I don't have xorg configured properly I can't go through synaptic to get the drivers. How do I uninstall the old ATI driver and install the new nVIDIA ones through the command line.

I have an ASUS N7600GS Silent, which is based on the nVIDIA 7600GS if that helps.

Thanks in advance:D

---

### Post by overdrank on 2007-08-21
> **tprzepiorka said:**
> Hello,
I finally got my graphics card working after switching from ATI to NVIDIA. Since I don't have xorg configured properly I can't go through synaptic to get the drivers. How do I uninstall the old ATI driver and install the new nVIDIA ones through the command line.

I have an ASUS N7600GS Silent, which is based on the nVIDIA 7600GS if that helps.

Thanks in advance:D

Hi you should be able to just reconfigure your xorg with 
```
sudo dpkg-reconfigure xserver-xorg
```
And if all else fails choose the vesa for the driver.

---

### Post by Gwasanaethau on 2007-08-22
> **overdrank said:**
> Hi you should be able to just reconfigure your xorg with 
```
sudo dpkg-reconfigure xserver-xorg
```
And if all else fails choose the vesa for the driver.

I wish I knew that last week - identical card with identical problems! Oh well, I'll know for next time! ;):lol:

---

