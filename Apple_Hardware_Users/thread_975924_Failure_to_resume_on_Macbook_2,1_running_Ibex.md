---
title: "Failure to resume on Macbook 2,1 running Ibex"
date: 2008-11-08
forum: Apple Hardware Users
---

### Post by Rog-Mahal on 2008-11-08
Over the past few days I've noticed that my Macbook has consistently failed to resume from suspend. It suspends normally, but when I try to wake it up, the back light comes on and the cd drive spins like normal, but all I get is a blinking underscore on the screen and a total system freeze. I believe the problem happens more frequently when I am running on battery, but I am not sure. I found a bug [here]("http://https://bugs.launchpad.net/ubuntu/+source/linux/+bug/205072") that seems to relate to the problem, although I have a different model. Has anyone had similar problems/ have a fix?

---

### Post by cyberdork33 on 2008-11-08
try unloading your wifi driver before suspending to see if that allows resume.

---

### Post by Rog-Mahal on 2008-11-08
Well, that did the trick so far. Is there a workaround for it other than unloading the module?

---

### Post by Rog-Mahal on 2008-11-09
After leaving it asleep overnight with the module unloaded, I got the same blinking underscore and failure to resume.

---

### Post by cyberdork33 on 2008-11-09
> **Rog-Mahal said:**
> After leaving it asleep overnight with the module unloaded, I got the same blinking underscore and failure to resume.
maybe there is another module giving problems too. I think you can specify modules to unload before suspend in /etc/default/acpi-support

---

### Post by Rog-Mahal on 2008-11-09
Hmm, would dmesg or some other kernel log be able to give me some insight into which modules could be causing the problem? I found that simply disabling wireless before suspending (as opposed to unloading the module) worked for my last cycle. Thanks for the tip.

[EDIT:] Upon looking at the file I found this:

```
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
```

Can I add a MODULES_BLACKLIST or something of that sort?

---

