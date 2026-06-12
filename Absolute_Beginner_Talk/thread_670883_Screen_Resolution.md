---
title: "Screen Resolution"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by PZJM on 2008-01-17
Hey Folks, I'm back to try this again.  Previously I had a bear of a time trying to create a dual boot system.  However, I was able to rebuild an old system that has an onboard graphics card.  My problem is that when i try to install Ubuntu the screen resolution is too large.  My options are very limited as to what I can change the screen resolution to.  I think the best I can get is 800x600.   I am not able to resize the windows to finish the installation.  Can anyone help?

I'm thinking that I need the drivers for the onboard graphics card, however, if I can't install Ubuntu then how do I install the drivers for the card?  BYW my onboard graphics is Nvidia

thanks....

---

### Post by rexxxlo on 2008-01-18
if you hold down the alt key and click the mouse you can move the windows to see the buttons

---

### Post by nikoPSK on 2008-01-18
maybe xorg got messed up? Can you go to System->Preferences->Screen Resolution and change it? If you want to reconfigure xorg and see if that works try this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

nikoPSK

---

### Post by jleaker01z on 2008-01-18
So...you dont have the nvidia graphics drivers installed from what I see.  Go to your package manager (Applications>Add/Remove programs) and search for nvidia.  You will see 2 driver packages, one called 'legacy'.  If you have an FX or later, you don't want the legacy drivers, get the other one.  The legacy drivers are for the Rage, TNT etc older series of cards.

Alternatively, you could go to nvidia.com and download the latest drivers they offer.  But that takes a bit more to install, albeit not much.

---

### Post by PZJM on 2008-01-18
Thanks for the tips.  I'll see what I can do tomorrow.

---

