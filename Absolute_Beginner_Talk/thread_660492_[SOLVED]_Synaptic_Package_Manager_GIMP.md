---
title: "[SOLVED] Synaptic Package Manager/ GIMP"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Valthinos on 2008-01-06
Some of you might have read my other post: [http://ubuntuforums.org/showthread.php?t=660434](http://ubuntuforums.org/showthread.php?t=660434) (thanks for all the responses btw), I got some comments back about installing wine to play games. I started up Synaptic Package Manager to try and install the program but i get the error: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What should I do?

Also, I tried to open a jpeg image from GIMP and I get the error: JPEG image plug-in could not open image.

Any help would be appreciated. Thanks!

---

### Post by oldos2er on 2008-01-06
Run 'sudo dpkg --configure -a'

---

### Post by taurus on 2008-01-06
Close synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by Valthinos on 2008-01-06
Thanks a lot! Problem solved for Synaptec! Anyone know how to fix my GIMP problem?

---

### Post by ubuntu27 on 2008-01-06
> **Valthinos said:**
> Thanks a lot! Problem solved for Synaptec! Anyone know how to fix my GIMP problem?

Weird. Try reinstalling GIMP.

open Synaptic, and search for GIMP. mark for Re-install, and then click apply.

---

