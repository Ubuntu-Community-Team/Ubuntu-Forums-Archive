---
title: "home webserver (apache2) help!"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-10-24
if you look at [www.kviero.com](www.kviero.com) it loads, and loads, and loads, and eventually gives up. if you look at [http://71.70.131.6](http://71.70.131.6) (my external ip) it works. if you look at this: [http://www.dnsstuff.com/tools/dnsreport.ch?domain=kviero.com](http://www.dnsstuff.com/tools/dnsreport.ch?domain=kviero.com) it shows you where it gives up. 

i have my godaddy domain pointing it name server guns at my external ip, and my web server has bind dns if it helps? 

by the way i am using ubuntu 7.10 server ed. CLI and Webmin.

---

### Post by bswilson on 2007-10-24
Any chance you have a desktop firewall (e.g., Firestarter) enabled, or do you have a router/firewall device blocking the DNS query traffic?

---

### Post by kevin11951 on 2007-10-24
i have the latter

---

### Post by kevin11951 on 2007-10-24
or at least i have a router, and i have it fowarding port 80

---

### Post by JeSTeR7 on 2007-10-24
Did you happen to just change the DNS entries for your domain at godaddy.com?  Sometimes it can take quite a while for the server to replicate to other DNS servers around the world.  Up to 72 hours in some cases.

---

### Post by kevin11951 on 2007-10-24
no its been set where it is for a few days

---

### Post by kevin11951 on 2007-10-25
someone please help!

---

### Post by bswilson on 2007-10-26
> **kevin11951 said:**
> or at least i have a router, and i have it fowarding port 80

OK, well, if your server is the nameserver, or if a nameserver is pointing to you, you might need to open udp/53 to allow queries coming into your system.  I admit I'm not an expert in DNS, though.

---

### Post by Dr Small on 2007-10-26
I thought that you had to edit /etc/hosts and add something like the following:
```
*ipaddress*   *domain-name.here*
```

I could be wrong though.

---

