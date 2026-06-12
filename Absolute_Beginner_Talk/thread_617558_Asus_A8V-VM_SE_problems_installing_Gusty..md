---
title: "Asus A8V-VM SE problems installing Gusty."
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by 1976saint on 2007-11-19
Hi, I'm having problems with my installation. I had a foxconn nforce Matx but had to replace it. My only spare was a ASUS a8v-vm se.

Now when I boot and select either graphics install modes I get the following message a few minutes into the CD wurring. This is before I get prompted for language etc..

The Display Server has been shutdown about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting 2 minutes before trying again on display 0. This just repeats.

Now I thought this was a mobo hardware problem, so I installed XP and it was OK so now I'm not so sure. Ive downloaded the ISO again but still get the same message. 

Can anyone shed some light please?

Forgot to add that Kubuntu seems to be ok, I can get to the desktop and click install - ubuntu doesn't get that far!

Cheers Paul.

---

### Post by Ptero-4 on 2007-11-19
Looks like a DRM'd mobo issue. Some mobos are designed to block OS's on the criteria of spected pixel arrangements (in less technical terms, the mobo "asks" the GPU if it's drawing a Windoze or non-Windoze like GUI and if the GUI is non-Windoze like it assumes a non-M$ OS and refuses to boot), the reason Kubuntu booted is that the mobo confuses KDE with Windoze and lets you boot, but gnome being mac-like gets detected as a non-M$ OS and hence the reason why ubuntu won't boot.

My advice: stick to kubuntu, at least until you get a better mobo.

---

### Post by aqchat300 on 2007-11-19
meh from what i hear asus and ati are anti linux ati has been working close to microsoft strange hmm? and asus is just  crappy board otherwise.. lol

---

### Post by 1976saint on 2007-11-19
Do you think adding a PCI-e GPU will correct the problem,  is the  mobo issue related to the onboard graphics?

---

### Post by Ptero-4 on 2007-11-28
> **1976saint said:**
> Do you think adding a PCI-e GPU will correct the problem,  is the  mobo issue related to the onboard graphics?

Maybe, if you stick a NVidia and ensure that the onboard GPU isn't running, and if it doesn't work you can always trick it with KDE.

---

