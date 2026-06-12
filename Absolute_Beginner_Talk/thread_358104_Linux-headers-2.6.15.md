---
title: "Linux-headers-2.6.15"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-02-10
So, my linux headers got updated to 2.6.15-28 (-386 and -686) today via Software Updates, and in doing so, my wifi driver (ndiswrapper) and my soundcard driver (w/ ALSA) was reset, so I had to re-install the files to the new kernel headers. I have 2 questions:

(1) Is there any harm in just uninstalling the new headers adn goign back to 27?

(2) If so, how can I copy where my drivers are in the last kernel (27) to the new one (28)? 'Cause it's really a pain to set up everything again each time the kernel updates.


Thanks!

---

### Post by jpeddicord on 2007-02-10
If I remember correctly, you should be able to just run `sudo modprobe ndiswrapper` and then `depmod` to fix the problem. You can also uninstall the linux-*-restricted-modules (or whatever the equivalent is in Dapper) to prevent the updates from installing new wireless drivers overtop of ndiswrapper.

---

