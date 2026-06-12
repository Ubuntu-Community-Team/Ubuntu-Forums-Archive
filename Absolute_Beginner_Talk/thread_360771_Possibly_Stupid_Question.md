---
title: "Possibly Stupid Question"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by orcalover on 2007-02-13
Okay, I realize that this might seem like a stupid question, and I think I already know the answer, but I just want to be sure...

I want to run and Apache/PHP5 server on my home box. I'm on a broadband cable connection with a dynamic IP address. Since I need a static IP in order to point my domain name to my server, I use dyndns.org for my DNS.

This all works fine, I have a single domain name which reached my Ubuntu server just fine. However, I want to use Name Based Virtual hosting in Apache so that I can have more than one domain name. I can add as many domain names as I want to my DynDNS.org account, but my question is this.

Do I need to install DNS and/or DHCP onto my Ubuntu server (which is actually the desktop box with Apache and PHP installed) in order for Apache to use name based hosting using only a single IP address?

Sean

---

### Post by Bachstelze on 2007-02-13
You can run your DNS server yourself if you want, it's a nice way to learn how things work. However, there are services that can do it for you, like [http://www.zoneedit.com/](http://www.zoneedit.com/)

---

### Post by tomane on 2007-02-15
> **orcalover said:**
> Do I need to install DNS and/or DHCP onto my Ubuntu server (which is actually the desktop box with Apache and PHP installed) in order for Apache to use name based hosting using only a single IP address?
No, you don't. Check the apache documentation, it has the answer to your problem and a lot more.

Virtual hosts for apache 2.0 is [here]("http://httpd.apache.org/docs/2.0/vhosts/name-based.html")
For apache 1.2 is [here]("http://httpd.apache.org/docs/1.3/vhosts/name-based.html")
and [here]("http://httpd.apache.org/docs/1.3/vhosts/name-based.html")  for v2.2

cheers,
--to.

---

