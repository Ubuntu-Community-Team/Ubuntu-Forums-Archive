---
title: "Squid Dansguardian Help"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by dacky on 2006-05-17
I have reached a high frustration level and need help.  I am trying to install squid, squidGuard and Dansguardian on Dapper running ltsp.  I cannot get dansguardian to work.  I have scoured the web for help  but cannot find a clear, step by step guide for install Dansguardian on Ubuntu that actually works!!!  I have not found any clear guide that does not leave out any steps (most is written for anything but Ubuntu).  Can't this be made a simple apt-get install?  I cannot figure out proxies or iptables.  Nothing works and I have tried hundreds of combinations.  Can someone point me to a [**B]clear**[/B] guide.  If this is such a popular program, there must be someone who has done it.  Too many late nights!

---

### Post by mjm115 on 2006-05-17
I searched and found a couple of sites:

[ttp://www.pilpi.net/journal/item-985.php](ttp://www.pilpi.net/journal/item-985.php)
[http://www.vollmar.ch/dansguardian-e.html](http://www.vollmar.ch/dansguardian-e.html)

You can also do a search in the forums.  Just search for "dansguardian" and you will find lots of help.  There are configuration files that you will have to edit in order to get it to work properly, or you could try installing webmin along with dansguardian so that you have a GUI to go along with it.

---

### Post by dacky on 2006-05-17
Thanks, that works, but I want to use squid because I also want to limit bandwidth.  I could not get my windows computer connected to Ubuntu to access the web this way either.  When I install squid, Dansguardian refuses to start up with the message:  "Restarting DansGuardian: Error connecting to parent proxy."  All the howto's I have followed lead me to the same problem.  If tinyproxy will work for limiting bandwidth, that will be ideal,  but I know squid has that capability.  So, I am still frustrated.

---

### Post by dacky on 2006-05-17
I should add, this computer will serve as a server for up to 50 computers, so the single user pc guides are also not what I need.

---

