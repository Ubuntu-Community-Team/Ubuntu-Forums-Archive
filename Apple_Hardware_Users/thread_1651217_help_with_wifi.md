---
title: "help with wifi"
date: 2010-12-22
forum: Apple Hardware Users
---

### Post by macfan34 on 2010-12-22
i just installed 10.10 on my white MacBook 4,1. i am unable to hook up to the wifi in  my home. any help?

---

### Post by skullmunky on 2010-12-28
can you tell which wireless card it is?

I think the 4,1 has a Broadcomm card which means it should be pretty easy to get it to work.  

[https://help.ubuntu.com/community/MacBookPro4-1/Lucid#Wireless (Broadcom)]("https://help.ubuntu.com/community/MacBookPro4-1/Lucid#Wireless (Broadcom)")

This is the "Additional Drivers" or "Restricted Drivers" manager, which you can find under the Administration menu.  In the past this has always required you to be connected by ethernet in order to download and install them - however, in my case with 10.10 on an MBP 6,1 I found to my delight that it just installed them magically somehow, and I had WiFi working almost immediately.

---

### Post by theSuperman on 2010-12-29
I have some issues connecting to wireless. For example, if I was previously connected to an AP using WEP encryption and switch to an open access point, it will not connect. I have to reload the driver. 

```
sudo modprobe -r wl
sudo modprobe wl
```

Obviously, check to see which driver your wireless card is using first.

---

