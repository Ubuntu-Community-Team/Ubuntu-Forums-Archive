---
title: "eth0 - Static - DHCP"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by sidneybarros on 2007-03-09
Well I am dumb - I have tried static IP, I've tried DHCP on the desktop with administrative privlidges. Nothing, Nada! 
Help!

It's a 3m card, 1 year old. Ubuntu sees it

Router does not require a MAC address and set for DHCP - (Linksys).

:confused: :popcorn:

---

### Post by bikeboy on 2007-03-09
Can you show us the output of this command through a terminal: Applications > Accessores > Terminal```
lspci
```

Or if it's a usb wireless adaptor try ```
lsusb
```
In both cases that's a lowercase "L" not an i or a one.

---

### Post by lhtown on 2007-03-09
I am not a networking expert, but with my ADSL provider, I have to enter the ip or some number (I set it on my router and have pretty much forgotten now) for my provider either in the router or on my computer.

Windows configured it automatically.

---

### Post by tagra123 on 2007-03-09
What is your routers ip?   192.168.1.1    (GATEWAY ADDRESS)

Make sure it is set in your network  settings.

To view or change network setting use the   Menu:  System-Administration-Networking

Click on eth0 properties.


Have you tried connectiong  to the router with the browser

[http://192.168.1.1](http://192.168.1.1)  or whatever your routers ip is.


If you can connect to the routers setup page then the network is working and chances are you might just need to enter the dns servers


In the network dialog -- opened above -- click on the DNS tab and add the dns servers.

I'll suggest opendns for these

208.67.222.222
208.67.220.220

Visit their site  opendns.com

---

### Post by sidneybarros on 2007-03-09
0000:00:0d.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev11)

---

### Post by bikeboy on 2007-03-09
Ok, it appears like it should work without problems on Linux which is good.

tagra123's suggestions above look good. If you're still having problems don't hesitate to post back.

---

### Post by halitech on 2007-03-09
> **sidneybarros said:**
> 0000:00:0d.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev11)

first time I've seen a MAC address thats basically 0's. are you sure the card didn't die on you?

---

### Post by lhtown on 2007-03-10
> 
In the network dialog -- opened above -- click on the DNS tab and add the dns servers.

I'll suggest opendns for these

208.67.222.222
208.67.220.220

Visit their site  opendns.com

Tagra 123,

A big THANK YOU!

I had been complaining for a while about a slow browsing experience (even though I get fast downloads and uploads). I just changed the dns settings for my router as you suggested and it now flies! I didn't realize that I didn't have to use my ISP's defaults.

*Goes off to browse the web*

---

