---
title: "Problem setting up firewall for a small business network"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by dlk on 2007-03-05
Hello all:

I'm trying to set up a hardware firewall for the non-profit where I work. We are connected to the Internet via SDSL and an EfficientNetworks DSL modem/router. I've sucessfully installed Ubuntu 6.06 onto the firewall machine, and I set up Shorewall and webmin to actually began the configuration process. But I'm stuck on what seems like an incredibly elementary question.

The docs for Shorewall re: configuring a two-interface firewall clearly state that the IP address for the external interface (eth0) on the firewall should be the static external IP given to us by our ISP. However, that IP is already in use by the DSL modem itself! Can I really also give that address to the firewall? I don't believe so, but I went ahead and tried it anyway. My Ubuntu machine just sort of froze up for a bit, then went back to using the non-routable internal IP address I'd given it earlier.

Other information that may be important -- we currently run NAT and DHCP directly on the router, and we only keep a few necessary ports open to the world. I'm assuming that I can keep NAT going on the router, and just redirect all traffic from those ports to the Ubuntu firewall, which will in turn use NAT to forward those packets on to the correct internal servers. I'm hoping that I can just leave DHCP service running on the router, even after the firewall is up.

Thanks for any guidance.

--David

---

### Post by STREETURCHINE on 2007-03-05
you could give this a read

[http://www.aboutdebian.com/proxy.htm](http://www.aboutdebian.com/proxy.htm)

[http://www.linuxguruz.com/iptables/scripts/rc.firewall_006.txt](http://www.linuxguruz.com/iptables/scripts/rc.firewall_006.txt)

---

### Post by dlk on 2007-03-05
Thanks for the reply. I'll definitely look over those pages.

A cursory glance at the first once (Setting Up A Debian Linux Proxy Server) seems to imply the same thing though -- that the external network interface of the firewall proxy server needs to be given a static external routable IP address. I feel like I'm missing some basic pieces of the puzzle, and once I have these, everything will fall into place, e.g.:

Is it possible to set up the DSL router without an external IP address, and give that address to the firewall instead? Or is it assumed that you have been given more than one routable IP address from your ISP?

It appears that every two-interface firewall must also by definition be considered a proxy server as well. Is this true?

Is it possible for the "external" IP address of the firewall to be one of the internal IP's as far as the router is concerned?

---

