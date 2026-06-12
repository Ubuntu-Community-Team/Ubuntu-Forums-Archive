---
title: "Slow Speed through a Proxy Server"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by ZuluboyRSA on 2007-07-01
Good day to All.

I have partially been successful in installing Ubuntu 7.04 as a Server as well as the desktop version on another PC . The desktop version was successfully setup with a dual boot (Vista and Ubuntu) using help from this forum. Thanks to those who posted the methods. A problem which is giving me grey hairs is as follows:-

Server was temporarily setup with an external public IP address connected directly to my ADSL router. The network gave me the full available bandwidth (up to 50K) when doing updates and package installs etc, using apt-get ....

My network, however needs to run through a HTTP Censornet (Debian based) Authenticating Server. As soon as I configure the Ubuntu Server or the workstation to work through the proxy, the bandwidth drops to a maximum of 3K and actually runs at an average of less than 2K. The Username used on Censornet Proxy Server for this PC has no bandwidth limits set. I have disbled ipV6 in Firefox as well as in aliases.  What am I doing wrong ?? Please help.

---

### Post by Maxtorm on 2007-07-03
It sounds as though the proxy is the issue as opposed to the Ubuntu boxes.  Do you have other proxy clients on the network that are getting the full 50K?  If you were really ambitious, you could install apache on the Ubuntu server box and configure it as a simple forward proxy temporarily connecting it directly to the ADSL line.  Then test the connection on the Ubuntu workstation using the newly created proxy.

---

### Post by ShiningRay on 2007-12-10
i've setup apache2 as balancing reverse proxy to mongrel cluster, but the proxy is too slow

---

