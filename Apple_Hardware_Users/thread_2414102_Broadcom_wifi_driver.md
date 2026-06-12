---
title: "Broadcom wifi driver"
date: 2019-03-05
forum: Apple Hardware Users
---

### Post by j3984 on 2019-03-05
When you load Ubuntu on a Macbook it doesnt have the wifi driver. I dont have access to ethernet...can I download the driver and put it on a usb drive and load it in 
Ubuntu that way? I am doing live sessions only...not installing permanently.

---

### Post by wildmanne39 on 2019-03-05
*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

### Post by kc1di on 2019-03-06
It may already be on the live usb you used to install the system.  It will depend upon which Broadcom card you have.  If it need bcmwl-kernel-source (Sta/wl) driver then you should be able to install it from the live usb stick.  boot up to the desktop with your installed system plug in the install media then navigate to folder pool then to Main then to g  the glibc install ```
/pool/main/g/glibc/libc-dev-bin_2.27-3ubuntu1_amd64.deb
``` with software installer first. Then install ```
/pool/main/g/glibc/libc6-dev_2.27-3ubuntu1_amd64.deb
``` now navigate back to pool Resticted>Bcmwl and install ```
/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb
``` Good luck.

---

