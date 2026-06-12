---
title: "MBP 3.1 &amp; nVidia driver problem"
date: 2008-09-06
forum: Apple Hardware Users
---

### Post by ZCos on 2008-09-06
I've been running HH on my MBP 3.1 relatively smoothly, however, I  got greedy and, against my better judgment, tried to enable desktop effects by downloading the nvidia-glx-new driver via Synaptic.  On reboot, I found myself with something like 800 x 600 resolution and haven't recovered yet.  I've removed nvidia-glx-new and tried both with and without nvidia-glx. Still no luck.

Kernel is 2.6.24.11 Mactel, although the same thing happens if I try booting into 2.6.24.19 Generic.

Any suggestions?

Thanks for your help.

---

### Post by ZCos on 2008-09-07
Rebooting in recovery mode and running xfix seems to have taken care of the problem (although it did wipe out my xorg.conf file).

---

