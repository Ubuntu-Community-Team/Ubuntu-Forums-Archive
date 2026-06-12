---
title: "Uninstalling Previous versions"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by kotty1216 on 2007-03-31
I have feisty installed on my laptop and when I start it up I see two different versions of ubuntu when I load grub. One is 2.something.20 and the other is 2.something.17 I think. I'm guessing the .17 is one that I don't need anymore so I was wondering how to uninstall it. Thanks to anyone that helps.

---

### Post by johnc4510 on 2007-03-31
Those are the kernels. I always leave one older kernel installed in case the current one has a problem with an update. That way I can boot to the older kernel to make fixes as needed. It's up to you though. It can be uninstalled via synaptic.

---

### Post by picpak on 2007-03-31
Kernel 2.6.17 doesn't even boot in Feisty, so it's pointless to have.

Open up Synaptic, and search for **linux-image**. Remove the one that's version 2.6.17.

---

### Post by johnc4510 on 2007-03-31
picpak is correct, I should have paid closer attention to your system.

---

### Post by kotty1216 on 2007-03-31
Okay, thanks I found all that and uninstalled the old versions.

---

