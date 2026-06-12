---
title: "Apache2 Web Server"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by jackiewky on 2008-03-18
Hi,
I am currently setting up my Apache2 web server in a LAN network. The problem is i only can access the web by the ip address of server but not the domain name [www.jackie.com](www.jackie.com). I already set the ServerName [www.jackie.com](www.jackie.com) in apache2.conf file. How can i access the web page by typing [www.jackie.com](www.jackie.com) on the computer in the LAN network?

Rgds,
Jackiewky

---

### Post by Oldsoldier2003 on 2008-03-18
> **jackiewky said:**
> Hi,
I am currently setting up my Apache2 web server in a LAN network. The problem is i only can access the web by the ip address of server but not the domain name [www.jackie.com](www.jackie.com). I already set the ServerName [www.jackie.com](www.jackie.com) in apache2.conf file. How can i access the web page by typing [www.jackie.com](www.jackie.com) on the computer in the LAN network?

Rgds,
Jackiewky
 
is your domain registered properly and the DNS set up to point to your server? right now it shows a parked domain page dealing with baseball...

---

### Post by jackiewky on 2008-03-18
Hi,
I didnt register any DNS with any DNS provider because i only want to run the web page in LAN which is not connected to the internet. Do I need to set up a DNS server in my LAN?

Rgds,

Jackiewky

---

### Post by freebeer on 2008-03-18
no.  Just add an entry in your /etc/hosts file.  It should look something like this

192.168.1.100 [www.jackie.com](www.jackie.com)

note: this is done on all the machines that will be accessing the Apache server, and the IP address would be that of the server.  It's best if you give the server a static IP so that you don't have to update the hosts file every time it changes.

---

