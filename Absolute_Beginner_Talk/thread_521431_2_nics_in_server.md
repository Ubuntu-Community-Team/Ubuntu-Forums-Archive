---
title: "2 nics in server"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by jengamac on 2007-08-09
This is a total newbie question...
I have a LAMP server running a small intranet portal.  I have a separate BSD machine running Squid.  Our users all have internet explorer set to use the proxy server IP (in other words it is not a transparant proxy) and all users have the intranet portal as their homepage.

 I want to find a way to have one machine run both the proxy and the web server..  But I don't want to go around and change settings for each user (homepage IP or proxy server IP).
So...
Is it possible to have a LAMP machine with two NICs with different IP's in the same sub net?  And would it be possible to have users access the apache webserver via one NIC IP address but also have Squid proxy running on the other NIC with the other IP address?

---

### Post by Rocket2DMn on 2007-08-09
Yes, you can define your static internal IPs first, then...  You can declare the IP address for apache to "listen *ip*" and "listen *port*" to in httpd.conf with the variable Listen.  I know less about squid, but it looks like in squid.conf you set "http_port *ip:port*".  Therefore you can have each listen on different IPs and ports if you wish.

---

### Post by jengamac on 2007-08-09
Rocket2DMn,
Thanks!!

I'll give it a try.  If it works I'll have saved myself a lot of time and running around.

---

