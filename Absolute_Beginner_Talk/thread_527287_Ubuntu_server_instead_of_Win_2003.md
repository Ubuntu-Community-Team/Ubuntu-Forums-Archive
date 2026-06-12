---
title: "Ubuntu server instead of Win 2003 ???"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by sajiv_k on 2007-08-16
I have been using Fiesty for couple of weeks and boy I'm damn happy with it.

We are setting up an office lan.

There would be around 9 users initially which may ramp up tp 35 in couple of months.

We were planning to use Windows 2003 server even though you have to pay an exorbitant price for it and also client access licenses for every device connected to the server...thats highway robbery :mad: !!!

After my experience with Ubuntu desktop I would like to use Ubuntu for the server, the problem is that I'm a complete newbie to Linux and the rest haven't tried it.

Would it be easy to configure Ubuntu server?

The server would have only basic functionalities like authorizing users on the office network, proxy server,firewall,anti virus  etc

The other machines would have Windows and one would be a Mac machine

Is there any tutorial available to help me with setting up this kind of network from scratch?

---

### Post by sad_iq on 2007-08-16
> **sajiv_k said:**
> 
Is there any tutorial available to help me with setting up this kind of network from scratch?
Try this and **research some more**:
 [https://help.ubuntu.com/7.04/server/C/](https://help.ubuntu.com/7.04/server/C/)   (Ubuntu Server Guide)
[http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7) (server discution)
[https://help.ubuntu.com/community/Servers?action=show&redirect=WebAndMailServers](https://help.ubuntu.com/community/Servers?action=show&redirect=WebAndMailServers) (Ubuntu Documentation)

---

### Post by praet on 2007-08-16
I would say start with:
[http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)

You have may options to do what you are asking, but you should really customize your server to do what is needed and none of the extra stuff.  For example, if you are not planning to run a website from it, why install web server software?  You could always use another internal machine for apache/mysql etc.

Here is the documentation page for server apps:
[https://help.ubuntu.com/7.04/server/C/](https://help.ubuntu.com/7.04/server/C/)

Generally, you can provide a DHCP server (or use a router to set IP addresses internally), DNS server (to cache dns requests, or leave it to your isp), LDAP for authentication, squid to proxy outbound web requests, internal email server, shared printers, samba fileshares, on and on and on...

Get acquainted with the options available, figure out what the needs of your users will be, then take that and match up a working system.

Good luck.

---

### Post by sajiv_k on 2007-08-16
Thanks sad_iq and praet that was fast :)

Lemme now go thru all the links and experiment with the machines

---

