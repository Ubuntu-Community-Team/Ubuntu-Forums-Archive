---
title: "Linksys router and proxy server"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by linuxcity on 2006-01-10
I'm new to Linux and would like to setup Squid Proxy for my community. We are currently using Linksys RV042 DSL Router to provide DHCP to all users in the house. I would like to setup a Squid Proxy server to block unwanted sites (pornography).

Where should I place the proxy server? I still like the Linksys DSL router to provide DHCP for all clients and be able to remotely control the router?

I have a system configured with two NICs ready to install Squid Proxy.

Any suggestions and technical help would be appreciated.

---

### Post by nihilocrat on 2006-01-10
Set up the box in between the router and your cable/DSL/whatever modem. This means, connect one NIC to the router's WAN port and the other NIC to the modem. Make sure you set up seperate interfaces for each (eth0 and eth1, most likely). Unfortunately, I don't know much about using computers in lieu of 'network appliances', so I'm not sure how you would configure your computer to correctly let all internet traffic to pass through (except port 80, of course).

---

### Post by linuxcity on 2006-03-08
I eliminated the Linksys router and put in Icop 1.410, which works very well.

 IPCOP Proxy Firewall Router

This is the necessary packages to create an Ipcop Proxy Firewall Router

[http://www.ipcop.org/](http://www.ipcop.org/) Linux firewall with Squid Proxy
[www.advproxy.net/](www.advproxy.net/) The Advaned Web Proxy add-on for Ipcop
[www.urlfilter.net/](www.urlfilter.net/) Ipcop add-on filter to manage content and IP filter
[http://cri.univ-tlse1.fr/documentations/cache/squidguard_en.html](http://cri.univ-tlse1.fr/documentations/cache/squidguard_en.html) Squid Guard information page.
[ftp://ftp.univ-tlse1.fr/pub/reseau/cache/squidguard_contrib/blacklists.tar.gz](ftp://ftp.univ-tlse1.fr/pub/reseau/cache/squidguard_contrib/blacklists.tar.gz) download filter black list

---

