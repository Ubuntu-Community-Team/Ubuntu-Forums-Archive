---
title: "really poor video performance with a Radeon 9250, and failed Envy driver install?"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by ijason on 2008-02-10
hey there.

i'm rebuilding my desktop with the addition of a donated video card. it's an ATI Radeon 9250, and i'm getting wretched performance on my machine now. the resolution setting doesn't list the native resolution for my lcd display, even though the xorg.conf has it listed, and i'm getting trails when  move windows around. unfortunately, my old card had restricted drivers that i simply needed to enable, but no such luck with this new one.

after skimming the forum, i followed the suggestion to download Envy and let it do the driver upgrade for me. i got this error message from it :

> python pulse.py ati
root@jason-desktop:/usr/share/envy# python pulse.py ati
Envy - Version 0.9.10
Ubuntu Gutsy 32bit
ENVY ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardware detection failed. You can try the manual installation at your risk.


is the Norwood Micro version of this card especially unfriendly to ubuntu? or have i missed something simple somewhere?

---

### Post by john.nicholls on 2008-02-10
For what it's worth, my (HIS) Radeon 9250 works perfectly with the supplied Gutsy driver, at a native resolution of 1280x1024.

---

### Post by spiderbatdad on 2008-02-10
> **john.nicholls said:**
> For what it's worth, my (HIS) Radeon 9250 works perfectly with the supplied Gutsy driver, at a native resolution of 1280x1024.

Correct. The fglrx nor envy driver will give you good graphics acceleration. You will most likely not be able to use compiz-fusion satisfactorily with that card. I'm not sure why. In Fiesty with Beryl the older ATI card worked great.

---

### Post by ijason on 2008-02-11
@**spiderbat** : think i should just use fiesty? instead of gutsy?

---

