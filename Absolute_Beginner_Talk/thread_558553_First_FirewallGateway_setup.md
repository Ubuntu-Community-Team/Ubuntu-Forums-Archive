---
title: "First Firewall/Gateway setup"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by dgcarter on 2007-09-24
I've been setting up an internet gateway / firewall, using two NIC's etc.  I'm amazed how simple this actually was, except the the firewall got a bit confusing, but thats all been solved.

Anyhow, here's my situation, I have two servers...

Gateway (192.168.0.1) this runs Squid, Firewall, Bind, etc.
Server01 (192.168.0.2) this runs Mail, IIS etc.

It should be noted that I have a dynamic public IP, so I use dnsExit to solve this.

I want to redirect a subdomain to Server01, so [WWW.woteva.com](WWW.woteva.com) much go to Server01 and MAIL.woteva.com must go to Server01

I am getting mail in and out of the mail server (Server01) did that with port forwarding on the firewall, but how can I do that with web traffic?

thanks in advance!

---

### Post by hyper_ch on 2007-09-24
you need to install a dns server on your gateway that will router queries to domain.com to a specific IP addres.

You may want to have a look here: [http://www.howtoforge.com/two_in_one_dns_bind9_views](http://www.howtoforge.com/two_in_one_dns_bind9_views)

---

### Post by dgcarter on 2007-09-24
I am running bind, I've configured A records to send MAIL.woteva.com to Server01 and INFO.woteva.com to the gateway, but if i try access it from outside the network I get sent to the gateways apache server no matter what I've specified in bind. it does work internally tho.

Something I did notice was when I (Internally) ping INFO.woteva.com it resolves to 192.168.0.1 (the gateway IP) but when I ping MAIL.woteva.com it resolves 192.168.1.1 which is the address of the NIC on my gateway that connects to the router.

---

