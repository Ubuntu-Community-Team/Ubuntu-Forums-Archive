---
title: "confused:Problems with videocard on startup"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by boxercbuk on 2007-04-24
confused: ubuntu keeps telling me my video card is not installed correctly and won't boot into the desktop unless I revert back to the onboard graphics card the card is installed properly and works perfectly within xp The card is a Nvidia GeForce 6200

please help as it is a pain changing the card in the boot sequence and swapping my monitor over from one plug to the other and I darn't do the full install as I will not see the dual boot sequence
cheers

---

### Post by meney on 2007-04-24
Have you installed the Nvidia drivers for your card? Ubuntu should detect your card and give you the option to install them in 
**System -> Administration -> Restricted Drivers Manager**

---

### Post by tarpon_bill on 2007-04-24
Just use the card as is, default driver and then install the nVida driver as the other poster states. Once done it should be fine from there.

The driver selection is done in a file called XOrg.conf.

The restricted driver install should take care of all that. I have asystem with the same card, so there should be no problem with it.

---

