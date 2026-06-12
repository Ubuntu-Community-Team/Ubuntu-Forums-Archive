---
title: "Dhcp"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by abasel on 2007-06-11
Is there a link that will take me through the steps of configuring DHCP on the Ubuntu (dapper) Server edition?

How do I know if it's running?
If not, how do I make is an automatic service?
How do I set up the scopes and reservations?

---

### Post by HackingYodel on 2007-06-11
> **abasel said:**
> Is there a link that will take me through the steps of configuring DHCP on the Ubuntu (dapper) Server edition?

Why YES, there is!

Check out [http://ubuntuguide.org/wiki/Ubuntu_dapper#DHCP_Server](http://ubuntuguide.org/wiki/Ubuntu_dapper#DHCP_Server) for exactly what you are looking for.

To see if it's running try** ps aux | grep dhcp** or, my favorite, **top** in a terminal.  
Including it in your /etc/init.d/, from the howto, will make it automatic at boot.

Hope that helps!

---

### Post by abasel on 2007-06-13
When I run 

ps aux | grep dhcp

I get 
var/run/dhcpclient........ etc

I then try and run 
sodu apt-get install dhcp3-server

only to get told that udhcpd is going to be install, after which I get a "waiting for headers" followed by a timeout.

I would think that if one installs the server CD that DHCP would be automatically included as a running service.

I've tried the normal updates too..... but they don't work either.

My proxy settings are correct so I'm at a losss.... I'm really finding the trip into Linux quite painful.

---

### Post by HackingYodel on 2007-06-14
I'm installing Dapper Server on an old computer now.  Will post again as soon as I find the problem.

*** edit ***

Try the section on repositories from the page I posted.  I think that you only have the CD in you source list and that is causing the problems with unobtainable headers.

---

### Post by abasel on 2007-06-14
:D GREAT!!!! I have progress. I have now managed to install DHCP :-) There was a repository issue.. didn't like the NZ mirror.

Now I have another problem

invoke-rc.d: initscript dhcp3-server , action "start" failed.

Whereto now?

---

### Post by abasel on 2007-06-14
I've set up the DHCP as per

[http://ubuntuguide.org/wiki/Ubuntu_dapper#DHCP_server](http://ubuntuguide.org/wiki/Ubuntu_dapper#DHCP_server)

But still get an error..

I must so though that I'm feeling much better not the less :-)

---

### Post by HackingYodel on 2007-06-15
What is the error when you issue this command:  **sudo /etc/init.d/dhcp3-server restart**

The **INTERFACES="eth0"** line from the guide may need to be **INTERFACES="eth1"** or **"eth2"**, or different all together.  Type **ifconfig** or **sudo ifconfig** to see which interface you should set here.

---

### Post by abasel on 2007-06-17
I don't really get an error... all that happens is that [fail] appears next to * Starting DHCP server.

ifconfig tells me that it's eth0

and my INTERFACES is set up correctly.

Any other ideas?

---

### Post by abasel on 2007-06-18
Sorted.... I hadn't given the server a static IP :-)

---

### Post by HackingYodel on 2007-06-19
Awesome!

I was at a complete loss as to what the problem could be.

Enjoy your new Ubuntu server!

---

### Post by abasel on 2007-06-19
Thanks for your patient help :-)

---

