---
title: "help with re-installing native gutsy 7.10 wireless drivers please"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by md11driver on 2008-02-19
i ran a script with the intent of making a usb wireless device work in my old laptop. i already had a working pc card wireless device which worked without having to use ndiswrapper.  the script removed all my native wireless drivers and now the pc card is not recognized. can someone help me re-install the native wireless drivers that are included in the 7.10 disk in order to save me doing a complete gutsy re-install?  i have a text gutsy 7.10 install disk available.  i have an idea i can do it from terminal but don't know how to proceed.

thanks a million in advance.

---

### Post by amingv on 2008-02-19
There's many things a script can do, so there's no easy way of telling how to go back without knowing what the script did in the first place.

It probably didn't delete the drivers, but maybe it blacklisted them (cat /ect/modprobe.d/blacklist) or disabled the interface (sudo ifup <interface>).

Do you know what driver your card used before the modifications?

---

### Post by md11driver on 2008-02-19
thanks, amingv.  good idea on the blacklists, but i didn't find anything there.  ifconfig just gives me info on "lo" and nothing else.  i don't know which driver my d-link 1330 wireless pc card was using since it "just worked" after my initial ubuntu installation.  never had any occasion to look.  i'm sure i can reconnect with a re-install, but since i had some screen issues, i'm trying not to go through that process again.  any other ideas?

---

