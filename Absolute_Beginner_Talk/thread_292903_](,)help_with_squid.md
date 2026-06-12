---
title: "](*,)help with squid"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by fkeith on 2006-11-04
To all the Ubuntu linux gurus out there
need help in configuring squid.I recently just got a copy of ubuntu and hve installed it.I hve a windows 98 network with all other machines browsing through a router connected to a switch.I am trying to get the other machines to browse from the proxy machine and prevent access to certain sites using ACL's.The thing is i am not able to configure the squid.conf correctly.As the windows machines are not able to browse the net.I get the message of the squid proxy version running.My network is 192.168.1.1-192.168.1.49 with 192.168.1.49 as my proxy server.Also i also need the windows 98 machines to download their mails using pop3 port 110 and send mails using port no 25 through the linux proxy server and connect to mailserver on an external ip 210.211.X.X and then access their mails.can some one help me with a sample configuration file.

regards

](*,) fkeith

---

### Post by kidders on 2006-11-04
Hi there,

It's difficult to block access to specific websites with ACLs. You don't really get a great degree of control over what gets blocked and what doesn't. You could try something like dansguardian maybe.

By the way, why do you want to proxy SMTP & POP? Doing so is non-trivial and usually unnecessary.

**NB: PLEASE DON'T DOUBLE POST!**

---

### Post by fkeith on 2006-11-07
hi,

Is there a way i can use my ubuntu machine as a router
and block access to certain sites and also download
my mails.Something like ICS in windows.Is there anythinglike that which I can do in Ubuntu.:-k 

thanks for you prompt reply

Regards

keith

---

### Post by kidders on 2006-11-07
I imagine what you need (at least to start with) is iptables. It will allow your Ubuntu box to function as a router.

---

### Post by mollmann on 2006-11-08
To block certain web sites try using dansguardian at [http://dansguardian.org/?page=whatisdg](http://dansguardian.org/?page=whatisdg), and for a firewall I like Firestarter, because it's simple to use. Here's the link [http://www.fs-security.com/](http://www.fs-security.com/)

---

