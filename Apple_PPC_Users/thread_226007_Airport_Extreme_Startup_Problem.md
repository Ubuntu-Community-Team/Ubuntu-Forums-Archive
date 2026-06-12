---
title: "Airport Extreme Startup Problem"
date: 2006-07-30
forum: Apple PPC Users
---

### Post by billyfoxtrot on 2006-07-30
I'm having some issues at startup with my Airport Extreme card.  Often my system gets stuck at the stage "loading hardware drivers" during startup, and the only way to fix this is to remove the Airport Extreme card, start up without it, put the card back in after it finishes starting up (which freezes the computer), and restarting.  I don't know why this works.

Also, the only way I was able to actually install Ubuntu is if I removed my wireless card during the installation process.

Is there any way I can start up Ubuntu without having to physically remove the Airport card from my computer?

In case it matters, I'm on a PowerBook G4 867Mhz 12".

---

### Post by rasec on 2006-07-30
Do you get any debugging info when you insert your airport card? Maybe you installed a bad firmware for it.

Anyway, to prevent the airport extreme driver from loading add the following to your /etc/modprobe.conf (you may need to create the file if it doesn't exist).

[quote="/etc/modprobe.conf"]blacklist bcm43xx[/quote]

If you want to load the airport driver later on, you need to put a # in front of blacklist in the modprobe.conf.

---

