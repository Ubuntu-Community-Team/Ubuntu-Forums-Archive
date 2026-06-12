---
title: "static ip"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by psychobeauty on 2008-03-24
hello i have a WAN ip: 62.**.***.**

i want to have an ftp server but i dont know how to set an ip to the server computer..coz i have 3 computers and when i try [www.whatsmyip.com](www.whatsmyip.com) from all of them the ip its the same for all of them, 

can you help me with what to do to portforward that ip to only one computer?/

---

### Post by garyed on 2008-03-24
check out this site. [http://portforward.com/](http://portforward.com/)
It helped me set up my Apache server.

---

### Post by psychobeauty on 2008-03-24
it does not have my router there and im still confuse,can u expain me//??

---

### Post by joshrobinson on 2008-03-24
whats the model number of your router?

---

### Post by psychobeauty on 2008-03-24
it is a crypto f330

---

### Post by joshrobinson on 2008-03-24
your router is listed on that page, so your setting up an ftp server on an ubuntu machine, and its using your WAN ip address, now is this ftp for local connections, or is this for everyone on the internet to connect to?

if its for everyone on the internet, you need to tell the router that any connection to your ip, asking to connect to port 21(the standard ftp port) that they should send them to the pc running the ftp server

this link should give you a start on how to setup the port forwarding

[http://portforward.com/english/routers/port_forwarding/Crypto/F330/FTP.htm]("http://portforward.com/english/routers/port_forwarding/Crypto/F330/FTP.htm")

---

### Post by psychobeauty on 2008-03-24
ok thanks i think\ i done it... do u know also any good tutorial for configuring apache,

coz webmin is confusing

---

### Post by joshrobinson on 2008-03-24
i really have no experience with apache, sorry
do a few searches on this forum, or google.com to see what you can come up with

---

### Post by psychobeauty on 2008-03-24
my question is that now from all over the network if i type my WAN ip is it going tobe connected to the server pc???

---

### Post by joshrobinson on 2008-03-24
if your using the ftp over a network, you should just use your computers internal ip
if you want people to access the server from outside your network, you will need to use the WAN ip

---

### Post by update_manager on 2008-03-24
> **psychobeauty said:**
> my question is that now from all over the network if i type my WAN ip is it going tobe connected to the server pc???

It depends on how your router works. Connecting the the WAN IP will probably not work, but it might.

Check out this link for an explanation of port forwarding:
[http://en.wikipedia.org/wiki/Port_forwarding](http://en.wikipedia.org/wiki/Port_forwarding)

---

### Post by psychobeauty on 2008-03-25
no..it does not work..


i have a wan ip...i want to have a web server...how to i put a static ip in the server...??

---

### Post by Viruk on 2008-03-27
You don't necessarily need a static IP, you could use a service such as DynDNS to forward to your dynamic address. 

Have a look at [http://www.dyndns.com](http://www.dyndns.com) and [http://en.wikipedia.org/wiki/DynDNS](http://en.wikipedia.org/wiki/DynDNS)

Maybe that would help...

---

