---
title: "Wireless - fine one day, bad the next"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by corbypete on 2008-04-03
Why  does my wireless stop working for no reason?

Only way I can get it back into gear is to unisntall the driver and reinstall.

Really annoying, as its fine for a few hours and different reboots, then i turn ont he next day and theres no life from it?!

i dont use the ethernet, ideally i would want to stop ubuntu getting confused by disabling it - but how?

---

### Post by hellomoto on 2008-04-03
Are you using ndiswrapper?

Please return iwconfig when ur system on a netowork and also for when it has failed.


What card are you using? And how are you loading the driver?

---

### Post by privaterolf on 2008-04-03
Can you post the result of ```
lspci
``` in a Terminal?

---

### Post by hellomoto on 2008-04-03
yep and iwconfig when your connected

---

### Post by pseudo-random on 2008-04-03
First check your area: Microwave ovens, Cordless phones (2.4Ghz only), etc will interfere.
Use Kismet or Airodump-ng to identify other networks in the area.
If the channels are conflicting thats the problem. Make sure the networks are at least 2 channels apart since they overlap some.

---

### Post by corbypete on 2008-04-05
Hmm, works fine in MintLinux.... wonder what we can learn from this?

Wireless management looks the same?

---

### Post by corbypete on 2008-04-05
Spoke too soon, its not working now in mint either.  really annoying

Im in on the live cd, only way to get online, any way i can output the above details from here?

---

### Post by dstew on 2008-04-05
Quick suggestion: disable roaming. This helps sometimes with an irregular fault like this.

---

### Post by corbypete on 2008-04-05
yeah its all manual... even tried enabling the ethernet lan so i could give it a static address but no joy

i getthe same on mint linux

shame because EVERYTHING else is spot on....  roll on version 8 huh? (crashes for me currently but wireless great)

---

