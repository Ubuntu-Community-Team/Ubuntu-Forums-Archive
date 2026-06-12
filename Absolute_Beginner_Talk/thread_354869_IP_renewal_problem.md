---
title: "IP renewal problem"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by timlewis242 on 2007-02-06
I'm having a home networking issue that I'm hoping someone can help me with. I have 4 pcs on a home network (Linksys wireless router). Two are desktops connected by LAN and two are lap tops connected by wireless. Of the 4, one laptop and one desktop run Ubuntu 6.1

The problem I'm having is that once my network card on the laptop is up and running and I shut the computer off, it will not connect again. I discovered that the problem appeared to be that the laptop would not renew it's request for an IP address from the router and it would attempt to use the same one it used last time. Sometimes this was OK as long as another pc on the network had not already grabbed it, in which case it would not connect.

I have attempted to resolve this by assigning a static IP to each of the 4 in the hopes that they would no longer step on each other's toes but I still have the same problem and it seems like the only way to get my Gateway MX 3230 to reconnect after a power-down is by assigning a new static IP address to it and making it do a reconfig of wlan0. The network card is a Realtek RTL 8185 54M that Ubuntu installed a driver for during installation. I have tried to use the windows driver for this device but cannot get NDIS Wrapper to recognize the device, no matter which driver I attempt. I tried to install the Linux version of the driver from the vendor but get module errors complaining that the driver already exists, even when I try to remove it first.

I have accepted the fact that I am probably stuck with the driver I have and have used Linux long enough to be grateful that it works at all but I was hoping someone might have an idea on how to force my network card to renew it's IP address on activation.

---

### Post by riven0 on 2007-02-07
Okay, have you tried running this command when you start up?:

> sudo /etc/init.d/networking restart

If it works, you may want to write a simple shell script for it so you can just click on an icon to get your networking up and connected again. I did this on my laptop that kept losing the connection whenever there was a power outage.

---

### Post by timlewis242 on 2007-02-07
Thanks,
I'll give it a try. Where would I add that to get it to run on startup?

---

