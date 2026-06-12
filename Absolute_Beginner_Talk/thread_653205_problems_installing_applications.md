---
title: "problems installing applications"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by famleon on 2007-12-29
I installed Ubuntu 7.10 and I trying to set up some applications (Amorok, Rythimbox and GKTpod and in none of them I am able to install it form the add/remove applications, so I tried the synaptic manager (well I was trying) and it gives errors or not installed libraries that will not be installed because are not needed and can not be installed, so can not install this other applications, so what I can do to set up my Ipod as well Skype, VOIP software and other software for TV capturing

---

### Post by taurus on 2007-12-29
Sounds to me like you didn't have enough repos available in /etc/apt/sources.list.

Close Add/Remove.  Then, open synaptic, System -> Administration -> Synaptic Package Manager -> Settings -> Repositories, and put a check mark in front of all the lines except the last one, Sources code, and the CDROM in the window at the bottom.  Close it and click Refresh.  Now, see if you can install those apps again either with synaptic or Add/Remove.  Remember, you need to shut down synaptic first before you open Add/Remove.

---

### Post by famleon on 2007-12-29
yeap, that solve the issue, magic answers:lolflag::lolflag: again, thanks

---

