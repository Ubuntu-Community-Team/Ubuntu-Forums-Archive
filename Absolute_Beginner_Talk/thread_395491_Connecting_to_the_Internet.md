---
title: "Connecting to the Internet"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by StJimmy on 2007-03-28
ok, so i installed Ubuntu 6.10 two days ago, and i haven't been able to get a Internet connection on it, and I'm not exactically sure what the problem is. Some one told me I need the Linux drivers for my motherboard, i don't know if this might be the case. But also, im on sympatico high speed, with a speedstream 4200 modem, and i heard that they don't give support to Linux users (like technical support) so calling them didn't do me much good.

I found this [http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe#inst](http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe#inst) and I was wondering if it would help me at all, cause my ISP does support PPPoE.

any help would be greatly appreciated, thanks for reading.


edit: oh, also, i forgot to mention, i have a d-link di-604 router, but I've tried with, and without it, but i heard that sometimes a router/modem connection works better then a modem alone.

---

### Post by chili555 on 2007-03-28
Open up a terminal and do:```
lspci -v
```Please post back the part about ethernet. For example:```
Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
```We will get it going.

I assume this is a wired ethernet connection.

PPPoE is generally easier to set up with a router because you select PPPoE, put in the user name and password and the router's software does all the hard work. Then your computer sees an ordinary ethernet connection without the need for additional configuration. As well, routers generally provide another firewall between those nasty hackers and your computer.

Here is a link to the manual for your router and page 13 shows how to set up PPPoE. [http://www.usit.uio.no/it/hjemmekontor/dlink/di604_manual_204.pdf](http://www.usit.uio.no/it/hjemmekontor/dlink/di604_manual_204.pdf)

---

### Post by StJimmy on 2007-03-28
thank you so much chili555, I'll try this, but right now i only have 1 monitor, I'm getting another one sometime today, so I'll try this and let you know what i get :)

edit: chili555, thank you for the help, i got connected by simply going into my network tools, and looking at my Ethernet interface, and then configuring it for static ip, instead of DHCP. 

im posting this from ubuntu  :)  

good day

---

