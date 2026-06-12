---
title: "Having problems with GTS 250 in ubuntu 20.04"
date: 2021-03-18
forum: Apple Hardware Users
---

### Post by leifkielland on 2021-03-18
My install defaulted to nouveau which worked but only allowed for  1024x768, which is too low for a pleasant ubuntu experience it seems. So  I tried installing the suggested nvidia drivers (from "additional  drivers"). The install went ok and I rebooted. Now the login screen  comes up (even though I set it to "login automatically" during install,  and once I've typed my password the machine freezes.

 I have seen suggestions of hitting crtl+alt+F2 to get into terminal  from the login screen but this does not work for me. 
Also, if I just  start typing while on the login screen, but before having engaged with  the UI to type my password in. Just typing randomly, not in a text box.  Some strange graphical garbage starts appearing in the top part of the  screen. As if some strange distorted terminal is glitching though the  login screen.

 Does anyone have any suggestions as to what could be going on or how I  could go about getting this to work? 
The GTS250 is an old card by now, I  get that, but with the market the way it is I really cannot afford to  upgrade. Even a radeon r7 260x is fetching EUR 50-100 where I live. :(

---

### Post by CelticWarrior on 2021-03-18
Welcome.

All installations "default to nouveau" unless users select the option to install third-party drivers, firmware.codecs, etc. (This is a new feature, before users always had to install Nvidia drivers *a posteriori*).

The Geforce GTS250 is old indeed but still supported by the 340.xx branch of long term support drivers. Is this version the one you installed?

Please do NOT use auto login in any case and if the old card is installed in UEFI hardware you need to disable Secure Boot. Secure Boot prevents loading proprietary drivers even if correctly installed.

---

### Post by leifkielland on 2021-03-18
Thank you for the reply. I should have stated which drivers i installed. 340.108, yes. I am using a MacPro 1,1. So not only old graphics card, old all round. I don't know if these machines have something similar to secure boot enabled, and I doubt I'll be able to change whatever parameters Apple has set for the BIOS on these machines. I'll have to look around.
I have gone into recovery mode now and purged nvidia, so I'm back to nouveau (which works, albeit at a low resolution).
I did state during the install that I wanted to install 3rd party drivers etc. but I installed using the old MacPro graphics card (7800GT) which is no longer supported. I had to use this card in order to get the machine to boot from CD. Once install was complete I changed GPU and here I am. :P

PS: Why should I not use auto login?

---

### Post by slickymaster on 2021-03-18
*Thread moved to **Apple Hardware Users**.*

---

### Post by CelticWarrior on 2021-03-18
> [COLOR=#000000]I installed using the old MacPro graphics card (7800GT) which is no longer supported. I had to use this card in order to get the machine to boot from CD. Once install was complete I changed GPU and here I am. [/COLOR]

Geforce 7800GT is also still supported by the same driver.
You can try to reinstall the Nvidia drivers in Additional Drivers.

---

### Post by leifkielland on 2021-03-18
7800GT just produced complete garbage from start to finish. Even getting though the installation process was a chore. :/

---

### Post by leifkielland on 2021-03-20
I've not been able to find a solution to this so I formatted and installed Ubuntu Studio 20.04 instead. Not only did GTS 250 work perfectly at first try, even the 7800GT worked without issue. :)

---

