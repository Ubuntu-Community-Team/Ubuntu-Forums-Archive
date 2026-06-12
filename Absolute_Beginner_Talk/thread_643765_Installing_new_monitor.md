---
title: "Installing new monitor"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by neotasic1 on 2007-12-18
Hi,
       Quick question - 2 actually.  I will be installing a new LCD monitor in about a week.  (22inch wide screen).  Will my Gusty install recognise it and configure it or will I have to reconfigure it manually? (It is sure to have different resolution to current 17in 4:3 LCD).  If I need to do it manually, can anyone point me in the right direction?

Same question regarding new DVD burner - already have one installed, but will be adding another newer one to replace the ageing DVD ROM currently installed.  Any problems likeley?

Thanks again.

---

### Post by ajgreeny on 2007-12-18
It will depend on the monitor, your graphics card and the driver you are using for the card.  You may be lucky, but I think you will need to reconfigure the resolution with 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```  Good luck.

---

### Post by neotasic1 on 2007-12-18
> **ajgreeny said:**
> It will depend on the monitor, your graphics card and the driver you are using for the card.  You may be lucky, but I think you will need to reconfigure the resolution with 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```  Good luck.

Thanks for that - looking forward to all that screen real estate. I suppose if I break something, I will have the pleasure of exercising my mind and fixing it :lolflag:

Or at worst I get to keep both bits.

---

### Post by philinux on 2007-12-18
I cant imagine the dvd burner being a problem at all.

---

