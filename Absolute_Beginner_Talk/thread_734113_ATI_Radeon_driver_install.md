---
title: "ATI Radeon driver install"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by DennisOS2 on 2008-03-24
I've tried installing the restricted ATI driver on three fresh installs ......... all lost the desktop on reboot.  Tried the ATI driver from the ATI site still no joy.  After the install ATI config wouldn't work and of course the Catalyst Control Center wouldn't come up.  Is there anyone with a Radeon x600 that has the restricted or ATI proprietary drivers working?  Is there a 'zero' point (base state) before attempting a ATI proprietary driver?

Thanks

---

### Post by forrestcupp on 2008-03-24
Try doing it with [Envy](http://www.albertomilone.com/nvidia_scripts1.html) and see what happens.  Download Envy, install it, then run Envy and first choose to uninstall the ATI drivers to get back to a clean slate.  Then run it again and install the ATI drivers, and see if that gets you anywhere.

If you can't get to your desktop to even download Envy, boot to your recovery mode and type:
```
dpkg-reconfigure xserver-xorg
```
And choose the Vesa drivers.  That will get you back to the desktop.  Then you can do the Envy thing.  Hopefully it will get it done right.

---

### Post by Oldsoldier2003 on 2008-03-24
> **forrestcupp said:**
> Try doing it with [Envy](http://www.albertomilone.com/nvidia_scripts1.html) and see what happens.  Download Envy, install it, then run Envy and first choose to uninstall the ATI drivers to get back to a clean slate.  Then run it again and install the ATI drivers, and see if that gets you anywhere.

If you can't get to your desktop to even download Envy, boot to your recovery mode and type:
```
dpkg-reconfigure xserver-xorg
```
And choose the Vesa drivers.  That will get you back to the desktop.  Then you can do the Envy thing.  Hopefully it will get it done right.
+1
Most times envy does just fine. In fact what you just described is how I got the restricted mode drivers to work on my Gutsy->hardy upgrade

---

### Post by DennisOS2 on 2008-03-25
Thanks Forrestcupp and Oldsoldier.  Sorry, didn't put that in my post, but used Envy the last time and same problem.  Maddening.  I'm at the point of wondering whether I should get a newer ATI card??  

Any sense of how difficult its been to get the **_x600_** to work with restricted or ATI proprietary drivers?  I just don't see many posts about the x600.

---

### Post by Oldsoldier2003 on 2008-03-25
> **DennisOS2 said:**
> Thanks Forrestcupp and Oldsoldier.  Sorry, didn't put that in my post, but used Envy the last time and same problem.  Maddening.  I'm at the point of wondering whether I should get a newer ATI card??  

Any sense of how difficult its been to get the **_x600_** to work with restricted or ATI proprietary drivers?  I just don't see many posts about the x600.

I use the x300 and it works just fine. i don't see where there would be much difference tbh

---

### Post by Rocket2DMn on 2008-03-25
Check this out - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-44352176e719033e226dffcab95c6e2647bdb882](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-44352176e719033e226dffcab95c6e2647bdb882)
It shows you what you have probably already done, but it says you can follow the directions for Edgy as well, which is a little more interactive.

---

### Post by remali on 2008-03-25
I have a Compaq Presario 2540 notebook with ATI mobility radeon IGP 340M.
I downloaded Envy and uninstalled the drivers. When I try to install i get this log:

python pulse.py ati
root@galileo:/usr/share/envy# python pulse.py ati
Envy - Version 0.9.10
Ubuntu Gutsy 32bit
ENVY ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk.

I try to make manual installation and i have to choose between 3 versions:

1) 8.3
2) 8.40.4
3) 8.28.8

What do u thing I should do.:(

---

### Post by Rocket2DMn on 2008-03-25
remali, I think you may be out of luck with that card.  It is not a typical ati radeon card, so you probably won't get support with the proprietary drivers for it, and if the "ati" drivers don't give you great support, you're probably out of luck there.  You may not be able to have Compiz Fusion, I think you would be fortunate to get your monitor's max resolution and be able to play videos.
If you have more concerns with this card, you should start a new thread rather than hijacking this one :)
Good luck.

---

### Post by remali on 2008-03-25
OK, thank you for the reply and sorry for the highjacking :confused: ):P

---

