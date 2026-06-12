---
title: "Port Forwarding Aiport Extreme"
date: 2007-12-30
forum: Apple Intel Users
---

### Post by Black Mage on 2007-12-30
I have an APACHE set up on my Mac down downstairs with webpages and I have set the server to a static. On my airport extreme, I set in port mapping, port 80 to the static IP address, and I also have a [www.no-ip.com](www.no-ip.com) for my non-static isp address.

It works fine if I'm behind the airport extreme firewall, so I can access by using the server's ip address, 192.168.1.30, or by going to my [www.no-ip.com](www.no-ip.com) url. But whenever I try to access when I'm not behind the firewall, for example I use my nieghbors wireless and use my [www.no-ip.com](www.no-ip.com) ip address, it doesn't work.

Can anyone help me with this? BTW, the server is my old PPC Mac running Ubuntu 7.04 server edition, LAMP set up.

---

### Post by opus_az on 2007-12-30
what happens when you're on you're neighbors wireless and you browse to [http://airport.extreme.public.ip](http://airport.extreme.public.ip) (WAN IP)

If that works then it's a DNS issue with your domain registrar. If that doesn't work then it's a problem with your port forwarding. Probably.

---

### Post by cyberdork33 on 2008-01-02
if the domain works on your lan, then the DNS is redirecting correctly. I would assume that it is a port mapping issue on your router.

---

