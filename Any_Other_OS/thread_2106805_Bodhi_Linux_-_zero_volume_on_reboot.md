---
title: "Bodhi Linux - zero volume on reboot"
date: 2013-01-20
forum: Any Other OS
---

### Post by BigSilly on 2013-01-20
Hiya. I'm currently running Bodhi Linux 2.0.0 on an old EeePC. I've recently performed all updates, and this seems to have pulled in the latest E17 packages. Fantastic! However, I'm having a volume issue I didn't have before. 

Each reboot sees the volume resetting to zero. I've tried alsamixer, sudo alsamixer, alsactl store etc. I've tried installing Pulse Audio and using paman, but nothing seems to work. The volume comes in at zero every boot and I have to manually set it.

What could it be, and how can it be fixed? Many thanks.

---

### Post by TenPlus1 on 2013-01-20
I have the same issue although on my desktop computer I turned compositing on/off and it somehow saved my current volume level after that...  Prolly just a flook but hopefully the bug itself will be sorted...

---

### Post by BigSilly on 2013-01-20
You're right. Turning off the compositor fixed the issue. Shame, as I was really digging the effects on such a dated spec. :D  Ah well, hopefully they'll fix it.

Thanks anyway. :)

---

