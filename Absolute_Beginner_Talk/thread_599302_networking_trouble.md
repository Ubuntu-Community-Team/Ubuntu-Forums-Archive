---
title: "networking trouble"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by hellomoto on 2007-11-01
hello, im trying to connect my desktop to our router using ubuntu 7.10

it shows up as Lan active on the router. If i go system>administration>networking i see "wired connection" undeneather the icon (that doesn't apear active) it says "roaming mode enabled" 

But I can't conect to the internet on the desktop. Can someone help me through checking my network settings and help me getting it working please.

---

### Post by meborc on 2007-11-01
open terminal... type```
sudo dhclient
```what is the output?

---

### Post by hoges on 2007-11-01
Roaming mode means that it's automatically assigning an IP address to the desktop given to it from the router. Is there a firewall on the router that could be blocking it?

You could try manually assigning the IP address. Untick the roaming box and type in the required info. If you need help with this post back.

---

### Post by ushills on 2007-11-01
Have you assigned a DNS server, test if you can ping the router address first, if so try pinging a domain such as [www.google.com](www.google.com), if this doesn't work check the DNS server address listed in the tabs under Network.

---

