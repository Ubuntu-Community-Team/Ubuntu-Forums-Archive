---
title: "Restricted drivers missing after update"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by BillGod on 2008-04-02
Running Hardy

just update with the latest updates.  After reboot video resolution was 640x480.  I checked xorg.conf it was totally re-written... no backup created..(thanks) I got my monitor reconfigured and tried to get restricted nvidia driver working.  I have restricted driver downloaded and installed per synaptic.  I even did a complete remove and re-install still will not work.  if I set xorg.conf to driver nv it get 1280x1024 just fine..  well xorg is using 80% of my processor.  If I set it to driver nvidia i get 640x480.  Modprobe  nvidia says failed to run nvidia install.(or something to that effect.)  restricted driver manager says no restricted drivers.  If anyone has any ideas let me know.

Thanks

---

### Post by joshrobinson on 2008-04-02
run apt-get update, then apt-get upgrade, and see if it says "restricted drivers" are being held back, that means they aren't able to be downloaded yet, other then that im not sure, im running 64bit, and the restricted drivers aren't available yet for my arch

---

