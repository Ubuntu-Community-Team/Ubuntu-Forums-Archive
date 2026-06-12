---
title: "Network trouble"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by dfrag on 2006-08-16
try'd the live cd to see what hardware works and what dont and found that my motherboards intergrated lan adapter is working, i can even ping web sites ([www.google.com](www.google.com), trace route ([www.google.com](www.google.com) & [www.applegeeks.com)](www.applegeeks.com)), even connect to my router configuration page through the browser. but the second i try to use any browser to navigate to a url that isn't a local file or the ip of my router, it wont get it, just sit's there for ages trying to connect and then displays a 404 type error. when through checked dhcp on the router, even gave it a static ip but still nothing.

Please help, i really want to use this os, but it's hinging on this and my grfx&sound card's working.

---

### Post by wieman01 on 2006-08-16
Can you post the content of this file?
> /etc/resolv.conf
This file controls the DNS and occasionally it does not get updated automatically. It should hold your preferred DNS' IP address (e.g. the IP of your router).

---

### Post by dfrag on 2006-08-17
ok, will insert the live cd again when i get home.

---

### Post by dfrag on 2006-08-17
Right i just run the live CD and run the "less resolv.conf" command in the ect/ dir

the output was
```
nameserver 192.168.0.1
ect/resolv.conf
```

that ip address is my router and its that, that handles DHCP.

---

### Post by steve.horsley on 2006-08-17
Try disabling IPv6 in Firefox. Open the URL **about:config** and search for **ipv6,** then double-click the entry to set disabled to true.

---

### Post by wieman01 on 2006-08-17
> **steve.horsley said:**
> Try disabling IPv6 in Firefox. Open the URL **about:config** and search for **ipv6,** then double-click the entry to set disabled to true.

But actually this is a bit strange... Disabling ipv6 would have been my first thought as well, but the problem occur when booting with the LiveCD. First time I hear of such problems in connection with that. 

Anyway, I suggest that you install Ubuntu and tackle your network problems later on. It's easier to come up with a solution in that case.

---

### Post by dfrag on 2006-08-18
ok wieman01, will do the install later today. (bloody work getting in the way of my fun)

---

