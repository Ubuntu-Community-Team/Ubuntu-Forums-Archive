---
title: "Starting an Apache Web server"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by ruddy on 2007-10-17
I have Apache 2 installed and it's listed as a running service, but I can't access the default "It works" page when I type in "http://localhost/". I have successfully implemented Apache servers in Fedora 6 and Open SuSE 10.3, but ubuntu has got me stumped. What have I overlooked?

Thanks.

---

### Post by Dr Small on 2007-10-17
Check out this page. Maybe you forgot something:
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

Dr Small

---

### Post by ruddy on 2007-10-17
I followed the instructions, and "http://localhost/" or "http://l127.0.0.1/" work now. How do I specify my IP address as the server name, so I can access the server from other PCs on my LAN?

Thanks,

---

### Post by JacobSteelsmith on 2007-10-18
You should be able to access it using the name of the computer, or the IP address, from other computers on your network. If you can't, check for a firewall on the router or the server.

---

### Post by ruddy on 2007-10-18
That won't work, because the Apache default is 127.0.0.1. I can't access it using the PC's IP address on the PC itself. 

Both Fedora 6 and SuSE 10.3 were far easier to set up than this is. I've been touting ubuntu for a while now, but I'll have to recommend SuSE for a Web server. 

Bummer!

---

### Post by hyper_ch on 2007-10-18
I don't see where your problem is...

from the machien apache is setup you call it by "localhost" or "127.0.0.1" - alternatively you do make an entry in your /etc/hosts file e.g.

127.0.0.1 domain.com


and from other computer you just enter the IP of the computer with the apache server in the browser bar

---

### Post by ruddy on 2007-10-18
There's already an entry like that in the hosts file. I know from the other two installations that you have to set the server name somewhere in an Apache configuration file. If you don't have a DNS name, you use the computer's IP address. I'm trying to find out where.

---

### Post by JacobSteelsmith on 2007-10-18
Here is a installation guide which talks about the FQDN (the ServerName setting).

[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html)

But a default installation should respond to all requests at http://<ip address>/ . Mine does. If it's not, my guess is a firewall somewhere or the service isn't started. You can check to see if the service is listening by using netstat -aN at the command prompt and look for port 80.

---

### Post by hyper_ch on 2007-10-18
from the other computers you add them also in thei /etc/hosts file...

Within the network the computer with apache on it should have a static IP address... assume that's  192.168.0.5

The other computers have ip addresses: 192.168.0.10 and 192.168.0.11

Then you will make entries in their /etc/hosts like:

192.168.0.5 domain.com

--> that will do the following. When entering in the browser "domain.com" it will not query the dns servers (your default dns server is your router as I suppose) but the computer will directly know that domain.com can be found on the computer with the ip 192.168.0.5 - which is your computer with apache.

---

### Post by ruddy on 2007-10-23
> **JacobSteelsmith said:**
> Here is a installation guide which talks about the FQDN (the ServerName setting).

[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html)

But a default installation should respond to all requests at http://<ip address>/ . Mine does. If it's not, my guess is a firewall somewhere or the service isn't started. You can check to see if the service is listening by using netstat -aN at the command prompt and look for port 80.

I got it! Thanks for the help.

---

