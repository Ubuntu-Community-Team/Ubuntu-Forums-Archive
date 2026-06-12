---
title: "Air Mac Express Internet Connection"
date: 2010-03-10
forum: Apple Hardware Users
---

### Post by yogiakira on 2010-03-10
Hi I've just successfully installed Ubuntu 9.10 to my imac using bootcamp.

Could any of you help me out connecting to internet? I'm using Air Mac Express but I don't know how to configure it to ubuntu.

Thank you.
Akira

---

### Post by R Ashton on 2010-03-10
Do you have the wireless card in your computer working properly? Not sure how to do the initial set up for an Air Mac Express (think you needed the mac util for it?) but if you've already set up your wireless network with the router you should just be able to join it.

---

### Post by linuxopjemac on 2010-03-10
you need to set the internal wireless card. Tell us what type of iMac you are using. You have to know the type of wireless card you are using.

To find out your type of wireless card issue the following:
```
lspci | grep -E "Atheros|Broadcom"
```


Some Atheros models work out-of-the-box with more recent kernels (ath9k); Broadcom chipsets all require non-free firmware, and thus require some user intervention.

---

### Post by Atilana on 2010-03-10
check your software, uninstall the driver and install again

---

