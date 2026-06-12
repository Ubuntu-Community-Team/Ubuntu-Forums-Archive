---
title: "Correct me if I'm wrong..."
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Dtree on 2007-04-17
Looks like I will be duel booting XP for some time yet~
I like the security of Ubuntu for office tasks, and the originality that can be customized into the desktop and arsenal of Apps and features available but Im having too many hardware issues too run it full time, 
IE:
I cannot locate support for my sound card / Audigy 2 ZS Plat  ( Is this in the works for Fawn?)
No support for my capture card (Canopus DV Storm2)  that I can find.

 And I have yet to find a way that works for me to mount all my SATA Raid drives, (I Have a couple terrabytes of premier project files on these drives that I cant afford to mess up trying less than clear methods)

So, it seems a lot of work to essentially (for me anyway) run a secure web browser. 
I suppose if your a developer or a casual user who likes to tinker then this is a great route, but to get everything configured on a system like mine in a timely fashion and without losing a lot of production time has been a humbling experience.
I want to thank the fantastic folks in this forum who have tried to guide me through this, Thank you!:) and I will keep my ear to the ground and who knows. maybe I will stumble onto the answers and get this thing off the windows  eventually. 
Im really getting sick of promising them that YES! This really is a legit copy! (4 times just in the last week or so)

Dennis

---

### Post by Skardal on 2007-04-17
According to [alsa-project card matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix"), your card uses the emuk10k1 driver, which is working very well! 

Maybe you could try running
```

sudo alsa-conf

or  ( see if your master-channel is muted! )

sudo alsa-mixer
```

:)

---

### Post by robenroute on 2007-04-17
> **Dtree said:**
> Looks like I will be duel booting XP for some time yet~

Dennis

Well, if you're struggling, you may as well call it duel booting.... ;-)

> **Dtree said:**
> And I have yet to find a way that works for me to mount all my SATA Raid drives, (I Have a couple terrabytes of premier project files on these drives that I cant afford to mess up trying less than clear methods)

Dennis

RAID is difficult, period. What I understand from you is that you've got a Windows system with a RAID holding terabytes of important data, and now you want to have these documents available under Linux. Wanting to do this on a dual-boot Windows/Linux system sounds like playing with fire. If you've got a back-up of the important data, just carry on trying and fiddling. But if such a back-up is not available, I would walk the safe route:
- set up a new (Linux) system with RAID
- copy the data to the new system (via network)
- test new system extensively (before possibly discarding the old one)

---

### Post by Dtree on 2007-04-18
> **Skardal said:**
> According to [alsa-project card matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix"), your card uses the emuk10k1 driver, which is working very well! 

Maybe you could try running
```

sudo alsa-conf

or  ( see if your master-channel is muted! )

sudo alsa-mixer
```

:)

Yep, re-configured and it works great. Have not tested everything yet but so far so good.
Thanks Skardal

And Thanks to you also Robenroute, sounds like the best advice.
Im putting together another box for dedicated audio only (Most of the parts arrived from Newegg today) and I will try installing fresh raids on it and then bounce the data back over the network.

Anyway, one step closer.
I have started searching again for any sign of hope to get my Canopus Dv storm2 card to work.
I would sure like to be the first kid on my block to have a Linux only setup....Yeah, Im that shallow :0

So, Thanks again for the info
Dennis

---

