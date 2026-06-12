---
title: "Can't ssh into or ping my domain without prefix"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by chrisdee on 2008-04-09
I can't http, ssh or ping my domain server (Ubuntu 7.10) from machines both inside and outside my LAN without the www prefix. If I write ping [www.mydomain.net](www.mydomain.net) or mydomain.selfip.net I can reach my server, but if I try without the www prefix or selfip part of domain name my server can't be found.

My server setup is the following :
- OS                   : Ubuntu 7.10
- Domain name  : mydomain.net (Network Solutions)
- LAN IP Server : 10.0.0.10
Gateway           : 10.0.0.1 (D-Link Gamer Lounge Router)
Router              : D-Link Gamer Lounge (connected between my cable modem and my LAN)
Dynamic DNS    : mydomain.selfip.net (Because I don't have a static ip from ISP I have a dyndns.com account)
/etc/hosts         : 10.0.0.10 mydomain.net  (content of my Ubuntu hosts file)
/etc/hostname : mydomain.net (content of my Ubuntu hostname file)

How do I get rid of the selfip name so I can http, ssh and ping my server with only my
domain name : mydomain.net. 
Any suggestions ?

---

### Post by Joeb454 on 2008-04-09
It should work, I have a domain (I'll call it blahblah.com :))

To ssh to it, I use ```
ssh joe@blahblah.com
``` does that not work for your username/domain?

---

### Post by chrisdee on 2008-04-09
Just now Im trying to ssh into my Ubunxu server with Putty (from outside my LAN). If I try [www.mydomain.net](www.mydomain.net), or mydomain.selfip.net  it works. If I try mydomain.net it does not work.


My /etc/resolve.conf file says :
search alfanett.no
nameserver 10.0.0.1

Might this have anything to do ?

---

### Post by gerscht on 2008-04-09
Is the name server configured to accept mydomain.net?
I my domain configuration (at uniteddomains.de) I have got an option to activate wildcard domains like *.mydomain.net which also includes mydomain.net

---

### Post by chrisdee on 2008-04-09
Maby this problem doesnt go under the Absolute Beginner Talk ?

---

### Post by chrisdee on 2008-04-09
How do I configure my name server to accept mydomain.net ?
Is this done on my account on networksolutions or at dyndns,
or locally on my Ubuntu server ?

If so wich files do I configure ?

---

### Post by mtbeedee on 2008-04-09
what do your DNS records look like.  Is there an A record for domain.com or just [www.domain.com?](www.domain.com?)

---

### Post by gerscht on 2008-04-09
It's something you will have to change at networksolutions or at dyndns.
As a quick fix, you can add the line 
```

123.45.67.8	yourdomain.net

```
to /etc/hosts (where 123.45.67.8 is the IP address of the server)
```

sudo gedit /etc/hosts

```
this will make the server available via yourdomain.net from this specific machine.

But as said before, if you want a global fix, you will have to change settings at networksolutions.

Hope this helps

gerscht

---

