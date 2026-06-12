---
title: "ubuntu eroor"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-01-11
i am bored of usind windows vista. i uninstalled it and installed ubuntu 7.10. when i wanted to enable effects i selected the extras option in visual effects. but it says it couldnt be enabled. i have 2 gb ddr2 nvidia 8800 ultra intel core 2 duo processor. is it enough? if yes then what is the error?

---

### Post by adi_das on 2008-01-11
sorry for the mistakes

---

### Post by Tyche on 2008-01-11
> **adi_das said:**
> i am bored of usind windows vista. i uninstalled it and installed ubuntu 7.10. when i wanted to enable effects i selected the extras option in visual effects. but it says it couldnt be enabled. i have 2 gb ddr2 nvidia 8800 ultra intel core 2 duo processor. is it enough? if yes then what is the error?

The drivers that come with Ubuntu for the NVidia do not cover all the functions necessary to operate Compiz-Fusion, and other compositing programs.  You will need to enable the proprietary drivers to handle them.

Go to System -> Administration -> Restricted Drivers Manager and put a check mark in the "Enabled" box.  This may result in the downloading/installation of the driver, or the driver may already be available and simply waiting to be enabled.

Hope this helps

---

