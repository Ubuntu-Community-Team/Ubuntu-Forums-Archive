---
title: "Dell D820 Wireless Card holy @rap!"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by k8fox1 on 2008-01-15
I have a Dell D820 that needs the Broadcom 43xx driver. I am running Gutsy 7.10. Though the driver is listed under restricted drivers and appears to be installed, I have no wireless. As much as I have been impressed with Linux and Ubuntu I am ready to take a leap over the wireless issue! So many articles and solutions but I still have no wireless. I am a beginner at Linux but I am ready to give up. THIS IS NO DOUBT ROCKET SCIENCE!

Help??????????????

:(

---

### Post by bwhite82 on 2008-01-15
You need to install the package: bcm43xx-fwcutter via either Synaptic or apt-get. Then follow the instructions when prompted (use the link it gives you).


-Cheers

---

### Post by k8fox1 on 2008-01-16
Ok well the only solution was to delete the Ubuntu partition and reload 7.10 as well as the bcm43xx driver. That seemed to have fixed the issue,

---

