---
title: "Airport Card Led + Xorg"
date: 2009-10-15
forum: Apple Hardware Users
---

### Post by guybrush.d on 2009-10-15
Hi Guys,
this is my help request::popcorn:

I  have a wonderful ibook clamshell indigo powered with 80gb hd and 320 mb RAM
before getting xubuntu jaunty i tried different distro on it. Now it runs very well xubuntu
(i like xfce for this laptop). The xubuntu setup has recognized everything except the pcmcia airport, but goggling around i made it work and now i have everything working.
So what's the problem!?
1) when i tried suse for ppc the light of airport in the center-bottom of the lcd panel
    flashed, with ubuntu it doesn't work, my airport is recognized by ubuntu with airport 
    and orinoco modules plus i had loaded agere firmware in /lib/firmware and i'm able 
    to surf the web with wireless but the light is off. How can i turn it on?:confused:

2) Ubuntu has configured the xorg.conf automagically and works but goggling around i 
    saw some forums where people has speeded up a little bit the xorg. If i try to modify 
    the xorg.conf the xserver doesn't work anymore. I added the "r128" module and 
    normal section with graphic modes input device,etc.. but my xorg.conf appears 
    like this:

Section "Device"
    Identifier     "Configured Video Device"
    BusID     "PCI:0:16:0"
Option     "UseFBDev"   "true"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Monitor        "Configured Monitor"
    Device         "Configured Video Device"
    EndSection

it looks strange i have also linux on my desktop pc and it's very different, here the 
input device sections are missed, and the diplay modes too!!! Has anyone some good xorg configuration!?!:confused:

THANK GUYS FOR YOUR HELP LINUX NOWDAY REALLY RULES!!!!:P

PS.: Let me know if anyone needs help on configuring the airport i will help posting the tutorial. Ciao.:P

---

### Post by guybrush.d on 2009-10-16
Hi guys again,
just an addition i surfed the opensuse forum and i discovered the opensuse use the
b43 drivers to manage the airport card, i tried to install it but it didn't work the installation notes specified to enable some modules in the kernel to make the light work,
i checked the kernel and those module were compiled (i don't remember all but something like: CLASS_LED,TRIGGER LED and MAD1410), i've also blacklisted the orinoco and airport
modules and loaded the new requested firmware, but nothing! any clues?!?:confused:

---

