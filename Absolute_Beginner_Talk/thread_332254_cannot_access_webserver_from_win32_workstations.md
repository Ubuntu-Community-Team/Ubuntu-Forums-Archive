---
title: "cannot access webserver from win32 workstations"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by socktan on 2007-01-05
****edit***
oh... my... lord...

I made recent network changes in my home office that changed my ip range from 192.168.0.* to 192.168.2.*.

Know that, can you guess my problem?  I kept trying to connect to 192.168.0.10 instead of 192.168.2.10.

No need to read further...

****edit****

I am having a problem reaching my freshly installed apache2 webserver @ 192.168.0.10 from win32 workstations on my local LAN.  The goal is to run a local development copy of my web site.  

The apache2 server is running.  I am able to browse phpinfo.php by pointing my browser on the ubuntu server to [http://127.0.0.1](http://127.0.0.1) or [http://localhost/](http://localhost/)

I have desperately searched through the forums in hope of finding an applicable solution to my problem.  It's is mostly likely something I have overlooked because I am an absolute beginner.

The ubuntu version is a fresh install from an ISO disc of 6.06 (dapper drake?).  I've applied all required updates via the automatic update manager.

I used *apt-get install apache2 php5 libapache2-mod-php5* to install apache.

So, please take pity on this beginner. I've spent exactly two beers trying to search and figure it out on my own... the best way to learn... right?.  I'm now looking to the community for help.

Thanks in advance,

--
Chris.

---

### Post by Bachstelze on 2007-01-05
[http://127.0.0.1](http://127.0.0.1) will only work if you try to browse the server from itself. From any other machine, you need to use the server"s LAN IP, which you can get with e.g. *ifconfig*.

---

