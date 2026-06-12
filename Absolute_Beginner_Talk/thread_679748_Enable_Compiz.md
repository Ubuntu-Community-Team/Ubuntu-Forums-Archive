---
title: "Enable Compiz"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-01-27
Sorry about this,

I would like to enable Compiz on my new Ubuntu desktop. I have a ATI Radeon X600 256MB HyperMemory graphics card with drivers installed from the Restricted Device Manager. I have also installed the Compiz Effects Manager.

When I go to enable them through the Appearence Preferences window I get an error message stating 'The Composite extension is not available' how can I fix this?

Thank you so much once again everybody.

---

### Post by FuturePilot on 2008-01-27
You probably need XGL
```
sudo apt-get install xserver-xgl
```
Log out and then log back it. They should work

---

### Post by Ub1476 on 2008-01-27
I don't think the X800 and below (which means X600 as well) need drivers from RDM. Uninstall those first, restart X (ctrl+alt+backspace/same as restart amost) and see if it works. If you can't get Visual Effects with the open-source drivers, install the driver from RDM again and XGL which can be found in Synaptic.

---

### Post by gruhland on 2008-01-27
Download the last version of Envy 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
and use it to uninstall your current video driver and afterwards install a new one. That helped me.

Good luck!

---

### Post by Crumpets and Jam on 2008-01-27
> **Ub1476 said:**
> I don't think the X800 and below (which means X600 as well) need drivers from RDM. Uninstall those first, restart X (ctrl+alt+backspace/same as restart amost) and see if it works. If you can't get Visual Effects with the open-source drivers, install the driver from RDM again and XGL which can be found in Synaptic.

Thanks!

---

### Post by freshspinach on 2008-02-10
Thanks! I finally got this awesome compiz radness working on my ATI x600, too!

---

