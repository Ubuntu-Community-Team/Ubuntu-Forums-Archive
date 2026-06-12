---
title: "Compiz &amp; 7.10"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by UKCamaroSS on 2007-10-19
Hi,

I've installed Ubuntu 7.10 and am trying to get Compiz working.... I understand it is included in 7.10.

Where do I go to start it (I can not see it listed by searching through the System, Preferences etc.

Thanks,

---

### Post by Pierre Lourens on 2007-10-19
The desktop effects setting are under "Appearance" which is found in "preferences".  There are three options: no effects, moderate effects, and full effects.  Typically, Gutsy enables moderate effects on compatible systems from the get-go.  Hope this helps!

---

### Post by William S on 2007-10-19
I also got the same problem. Where is it supposed to be?

---

### Post by UKCamaroSS on 2007-10-19
> **Pierre Lourens said:**
> The desktop effects setting are under "Appearance" which is found in "preferences".  There are three options: no effects, moderate effects, and full effects.  Typically, Gutsy enables moderate effects on compatible systems from the get-go.  Hope this helps!

Thanks, but I thought Compiz was "more" than what you get via the "Systems, Preferences, 
Appearance, Visual Effects" and then selecting "Extra". 

So as I have selected "Extra", does that mean I am now using Compiz?

---

### Post by Pierre Lourens on 2007-10-19
> **UKCamaroSS said:**
> Thanks, but I thought Compiz was "more" than what you get via the "Systems, Preferences, 
Appearance, Visual Effects" and then selecting "Extra". 

So as I have selected "Extra", does that mean I am now using Compiz?

Yes, if you see the wobbly windows and desktop effects, that is the compiz that is included with Ubuntu.  If you want more advanced features, you could try installing Compiz or Beryl from sourcem, but the desktop effects included in Ubuntu seem fine for most users.  Additionally, Gutsy's desktop effects are very stable on most systems.

---

### Post by techno-mole on 2007-10-19
you can enable compiz by the methods posted, however if you want to change anything or enable different stuff, like the ring switcher and so you will need the compiz settings manager, which from what i have heard isnt installed by default, try running this code in terminal.
```

sudo apt-get install compizconfig-settings-manager

```

after that run ```
 sudo apt-get update
```

then, providing that it installed ok you can go to  - system - preferences and you should see something like "advanced desktop effects settings" or compiz config settings manager, if you open that up you can change just about everything from what effects run to the key bindings that control them.
hope this helps.
cheers

---

### Post by UKCamaroSS on 2007-10-19
> **Pierre Lourens said:**
> Yes, if you see the wobbly windows and desktop effects, that is the compiz that is included with Ubuntu.  If you want more advanced features, you could try installing Compiz or Beryl from sourcem, but the desktop effects included in Ubuntu seem fine for most users.  Additionally, Gutsy's desktop effects are very stable on most systems.

OK, cool - it's running, Thanks.

---

### Post by Duck2006 on 2007-10-19
If you go to Synapic Pack Manager you can load compiz from there.

---

