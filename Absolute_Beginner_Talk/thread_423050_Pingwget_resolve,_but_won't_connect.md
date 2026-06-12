---
title: "Ping/wget resolve, but won't connect"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by mindstorm23 on 2007-04-25
Hello,

I am setting up a web server behind a DMZ on my network.  However, I can't access the internet to apt-get update or install due to connection timeouts.  When I try to ping or wget an arbitrary site (e.g. [www.google.com](www.google.com)) the name resolves (meaning DNS is working, though my DNS server is inside my network), but it won't connect.  Ping and wget will sit there until the cows some home idling away.

I have disabled ipv6, and I'm pretty sure that my firewall is allowing request from the server out.  It's a Cisco PIX Firewall.  I've been at it all day and I'm at my wit's end...help!

---

### Post by leibowitz on 2007-04-25
Please tell us your IP infrastructure.

Check what is your gateway on your webserver. Check all routes.

---

### Post by LaurelLynn on 2007-04-25
Dear mindstorm23,

If you have a computer that can download, I would try installing Ethereal.  It gives a really good picture of what is being exchanged between the systems.

For example, I work with lots of peope here who can''t get their broadband connection to connect.  It is because the ISPs DCHP server can take as much as 30secs to respond and most routers timeout at 15secs.  I know all this because Ethereal gives me the times, type and contents of every packet sent.

It doesn''t need to be on the server, only on the same network segment.

---

### Post by mindstorm23 on 2007-05-01
I never got it to work, but I took it off the DMZ and put it behind a different subnet (it's only internal), and it works, so I'm going to leave it.  Thanks for your help, though.

BTW, Ethereal is now Wireshark, I believe.

---

