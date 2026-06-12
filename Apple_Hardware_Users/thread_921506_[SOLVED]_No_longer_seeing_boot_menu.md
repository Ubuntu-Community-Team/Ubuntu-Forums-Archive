---
title: "[SOLVED] No longer seeing boot menu"
date: 2008-09-16
forum: Apple Hardware Users
---

### Post by holmrun on 2008-09-16
Hey guys, I have had Feisty installed on my 1.67 G4 powerbook for a year or so now and all of a sudden when I reboot I no longer see the boot menu. If I let the system go it will boot the default OS which is Feisty and if I press X every so often at the black screen after the 'gong' it will boot into Tiger like it is supposed to however I never see the menu any more. Any ideas? Nothing has been added to the system as far as the Feisty install goes - on the Tiger side just the apple updates. This is with the internal laptop screen - I have not tried with an external plugged in. 

Thanks!

EDIT: I am using yaboot - figured that was an important thing to mention.

---

### Post by tiresia on 2008-09-16
> **holmrun said:**
>  on the Tiger side just the apple updates. This is with the internal laptop screen - I have not tried with an external plugged in. 

Most probably updating Tiger changed the Open Firmware SetUp - have you update Tiger online or with a DVD?

Anyway you should be able to restore the previous situation just by running in ubuntu

```
sudo ybin -v
```

---

### Post by holmrun on 2008-09-16
Thank you Tiresia, I will give that a try when I get home! As for the Tiger updates, they all came from the apple software update tool inside of Tiger and were downloaded/installed with it.

---

### Post by holmrun on 2008-09-16
Thank you! That did the trick!

---

### Post by tiresia on 2008-09-16
Nice! Please, mark the thread as solved,

---

