---
title: "ICS/NAT linux host, win client"
date: 2005-08-26
forum: Absolute Beginner Talk
---

### Post by huzzzo on 2005-08-26
Hi there, 
I'm total new in Linux World, I've just installed Ubuntu 5.04  :) 
I've configured my adsl modem w/ pppoeconf and I'm writing from linux :D
My actual situation is this:
1 modem adsl
1 eth switch
3 computers (both win and linux)
All devices/machines are connected to the eth switch, so every pc has only 1 eth device.

My computer is the first and it connects direclty to the internet through adsl modem.
I wanna use my PC as router/firewall and allow other PCs to use internet (gaming and office use).
I've tried to read some tutorials but they not fit w/ ubuntu or I'm too noob to undestand.  :roll:  ](*,) 

Now I have assigned in linux, ip and gateway to my eth0 device (see below, are the same in windows).

So... what I have to do?
 
In windows DHCP assign to my pc:
gateway 192.168.1.1 (modem ip) 
ip 192.168.1.26 (eth ip)
subnet mask 255.255.255.224 

Thanks!

---

