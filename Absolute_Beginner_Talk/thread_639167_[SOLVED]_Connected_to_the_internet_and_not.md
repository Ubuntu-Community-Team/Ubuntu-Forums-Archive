---
title: "[SOLVED] Connected to the internet and not"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by bitra on 2007-12-12
Yesterday (without knowing exactly how, besides Ip number, etc.) I can connect to the internet using wired connection on my Gutsy Gibbon. But today, when I tried typing [www.google.com](www.google.com) on my firefox and tried to connect, nothing happen.

Is there any suggestions about what should I do?

Thanks.

---

### Post by daimaru on 2007-12-12
check that you have an ip assigned to your eth0 device (or the device name your using).
if you don't have an ip address assign one manually or through dhcp
```
sudo dhcpcd eth0
```
also make sure your nameserver is in your resolv.conf file
```
cat /etc/resolv.conf
```
there should be some entry like >>    nameserver 192.168.2.1 
or a different number (depends on what ip your router is on)
if its not in there add your routers ip as the nameserver. 

one more thing you can check is the route. in terminal type
```
route
```
that should list your routing table. your router's ip address should be listed there. eg. 192.168.2.1 
if not add a route to your eth0 device
```
sudo route add default gw 192.168.2.1 eth0
```

---

### Post by bitra on 2007-12-13
Thanks for the tips. I don't know why but now the internet connection is o.k.

I appreciate your help with it. I'm sure it will be very helpful if next time I get the same problem.

Thanks again.

---

