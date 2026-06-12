---
title: "Screen Resolution stuck in 5.10"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by qpackard on 2006-04-01
My screen resolution is stuck at 640x480 @60Hz which is the only resolution/refresh listed at System>Preferences>Screen Resolution. When I installed 5.10 I did not notice a screen where I was allowed to choose the resolutions. I have read where to alter the /etc/x11/xorg.conf file but when I examined that file there were seven resolutions at each Depth. 
How do I set the resolution and refresh rate? If there are permissions I need how do I change them?

---

### Post by alamba on 2006-04-01
If you're not getting the resolution you're looking for then it's probably a driver issue. What's your machine specs? Display card manufacturer?

A

---

### Post by SkimWear on 2006-04-01
have you installed the right drivers? mines only went up to 800x600 until I installed my ATI drivers, now my resolution goes waaaaaaay up.

like alamba said, post your card manufacturer.

---

### Post by qpackard on 2006-04-01
I think the information your asking about is this from the device manager:

nVidia
NV18 [GeForce4 MX - nforce GPU]
Bus Type: PCI
Device Type: unknown
Capabilities: unknown

The monitor is Samsung, SyncMaster 730B.

Does this help? Is there somewhere else I should look for information?

---

### Post by alamba on 2006-04-01
Google for linux drivers for NV18 and install them, that should fix the resolution issue.

A

---

### Post by SkimWear on 2006-04-01
you might also want to use the search feature on the ubuntu forums for information on where to get the drivers and how-to install them.

there may be previous articles.

---

