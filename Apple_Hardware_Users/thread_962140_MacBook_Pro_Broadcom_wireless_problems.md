---
title: "MacBook Pro Broadcom wireless problems"
date: 2008-10-29
forum: Apple Hardware Users
---

### Post by mxweas on 2008-10-29
I used sudo apt-get install b43-fwcutter to install the driver for my broadcom wireless card on my unibody macbook pro. How can I check that it is working? System > Administration > Hardware Devices still shows nothing and Network Manager shows only my wired connection...

Thanks,
Max

---

### Post by cyberdork33 on 2008-10-29
> **mxweas said:**
> I used sudo apt-get install b43-fwcutter to install the driver for my broadcom wireless card on my unibody macbook pro. How can I check that it is working? System > Administration > Hardware Devices still shows nothing and Network Manager shows only my wired connection...

Thanks,
Max
b43 does not work with that card, and others have stated that the wl binary driver from Broadcom also does not yet work. You are probably stuck trying to use ndiswrapper. These directions should work for ndiswrapper...
[https://wiki.ubuntu.com/MacBookPro/Penryn#Installing%20the%20Broadcom%20Wireless%20Driver]("https://wiki.ubuntu.com/MacBookPro/Penryn#Installing%20the%20Broadcom%20Wireless%20Driver")

---

### Post by mxweas on 2008-10-29
I installed the broadcom wl driver and it appears to work, the broadcom card in this laptop is supported by the wl driver. The only problem I have now is iwconfig and ifconfig show my wireless device as eth1. I believe this is causing problems as I can detect wireless networks but I am unable to connect to any of them.

Thanks,
Max

---

### Post by cyberdork33 on 2008-10-29
> **mxweas said:**
> I installed the broadcom wl driver and it appears to work, the broadcom card in this laptop is supported by the wl driver. The only problem I have now is iwconfig and ifconfig show my wireless device as eth1. I believe this is causing problems as I can detect wireless networks but I am unable to connect to any of them.

Thanks,
Max
No, it really doesn't matter that it is eth0. A lot of people have reported issues with connecting to an AP that has encryption enabled. Can you see if it works without? If so, then I would check for bugs in launchpad.

---

### Post by mxweas on 2008-10-29
I wanted to use airodump with this to pick up wifi packets but when I try to use it it says the wifi card is an ethernet adapter... Any ideas how to fix that?

Thanks,
Max

---

