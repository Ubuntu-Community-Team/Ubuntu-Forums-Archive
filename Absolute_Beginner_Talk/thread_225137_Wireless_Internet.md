---
title: "Wireless Internet"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by Touch.Code on 2006-07-29
OK, I am looking to change to Linux, but need to know this about the internet.

I have a laptop, with a Belkin; F5D9010. Upon trying the Live CD, to see if I could use the internet, it would not connect!

The Driver CD is only for Windows, what can I do?

---

### Post by ubuntuuser on 2006-07-29
There is a project called NDISwrapper. The program "wraps" around the windows drivers and makes Linux use these. It supports a lot of different cards, and will most likely also support yours. All you'll need is ndiswrapper and the windows drivers.

---

### Post by Touch.Code on 2006-07-29
OK, so where can I download this NDISwrapper? Will I need to run it on Windows/Linux?

---

### Post by Apple 101 on 2006-07-29
It just needs to run in Linux.  You will need *ndiswrapper-utils*, *wpa_supplicant*, *ndisgtk* (optional - need to enable Universe repository), wpa_gui (also in Universe).  They can be installed from Synaptic (System --> Admin --> Synaptic).  To enable the Universe repository, you need to check the box in the Repositories area of Synaptic.

Of course, all of these steps are far easier if Linux is actually installed on your computer, not just as a live CD distribution.  You should probably consider all of the options before installing though, in case you do not want Ubuntu.  Dual-booting is also easy.

---

