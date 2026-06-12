---
title: "Squid3 error connection failed 101"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by ahounsome on 2008-04-12
Hi, I have a new kubuntu machine running squid3 and cabled direct to the router. From my kubuntu wireless laptop I cannot go through the proxy to get onto the Internet. I have set the Http_access up to allow 192.168.0.0 ip's and set the proxy up with a fixed IP of 192.168.0.4. My laptop is running DHCP and has picked up 192.168.0.3. I get the following error:-

ERROR
The requested URL could not be retrieved

While trying to retrieve the URL: [http://www.linuxmint.com/start/](http://www.linuxmint.com/start/)

The following error was encountered:

    * Connection to Failed 

The system returned:

    (101) Network is unreachable

The remote host or network may be down. Please try the request again.

Your cache administrator is webmaster.
Generated Sat, 12 Apr 2008 11:37:22 GMT by localhost (squid/3.0.PRE6)

---

### Post by ahounsome on 2008-04-12
Ok no panic! I've had another look at the proxy and it wasn't pinging out. i changed over the IP from fixed to dhcp and everything worked. I configured the router to assign fixed IP's to the proxy and other machines on the internal network and all seems ok.

---

