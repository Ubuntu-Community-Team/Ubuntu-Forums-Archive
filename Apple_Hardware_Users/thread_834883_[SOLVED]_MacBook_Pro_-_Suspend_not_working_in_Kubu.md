---
title: "[SOLVED] MacBook Pro - Suspend not working in Kubuntu 8.04"
date: 2008-06-19
forum: Apple Hardware Users
---

### Post by violinmandan on 2008-06-19
I installed Hardy on my MacBook Pro (Santa Rosa I think) and most of the hardware works great, but suspend is not working.
When it tries to suspend, it gets all the way there (the light on the front even turns on), but it immediately wakes up.
Any suggestions?

---

### Post by undertakingyou on 2008-06-20
I was having some suspend issues.  For me it would suspend and then immediately come out of suspend.  It was rather annoying.  I added a couple of lines to /etc/default/acpi-support.  I changed ```
Modules ""
``` to say ```
Modules "sky2 ath_pci"
``` and that seemed to do it for me.

---

### Post by violinmandan on 2008-06-20
Thanks, that worked perfectly.
Now I don't have shut down my computer so often!

---

### Post by cyberdork33 on 2008-06-20
please mark thread as solved from the thread tools menu at the top.

---

### Post by hanzomon4 on 2008-09-06
I've having the same problem but I'm using the new ath9k driver. I've tried just about everything in that acpi-support script. Could you post yours so I can compare and contrast?

---

