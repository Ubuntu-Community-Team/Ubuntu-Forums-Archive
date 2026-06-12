---
title: "Can I safetly delete previous Linux headers?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by cogenthack on 2007-08-30
I have somehow ended up with 3  modules in lib/modules 2.6.17.10-generic 2.6.17.11-generic and 2.6.17.12-generic. I have deleted the first with no ill effects. Now, in usr/src there are the linux headers for .10 and .12, can I safely delete the older or will some packages compile against these headers?

---

### Post by stevebakerj on 2007-08-30
Why not just uninstall the kernels you don't want through Synaptic or Adept, this way Grub will be updated and you don't have to go through your system deleting files. However I would always keep at least 2 kernels (the current and the last known good one) on my system just in case an update breaks your current kernel.

---

### Post by nosfed438 on 2007-08-30
how do you do that in synaptic????

---

### Post by cogenthack on 2007-08-30
There were 3 linux entries in the boot list, I was under the impression that this wasn't right, and it was a screw up on my part. Thanks for the help

---

### Post by stevebakerj on 2007-08-30
> **nosfed438 said:**
> how do you do that in synaptic????

Just do a version search on 2.6.?? and mark the packages you want removed for removal.

---

