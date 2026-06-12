---
title: "apache server unreachable through router?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by galdren on 2008-01-06
Hi,

This'd be my first post on this forum, I really like this site and it has helped me figure out alot of stuff about ubuntu by reading the topics. Thanks!

But for this problem, I can't find a topic..

I've just installed the newest apache on my ubuntu 7.10 desktop. It is reachable through 127.0.0.1 and from within the network (192.168.1.1) but not reachable from WAN. I have a linksys WRT54G router, with my ip configured as DMZ. In XP and vista this used to work flawlessly (after configuring the windows firewall to allow listening on port 80). But here it doesn't work at all.

Can anyone help me with this? Is there some kind of port blocker? Or is apache configured to just allow internal connections?

Thanks in advance,
Mustafa

---

### Post by JimTDI on 2008-01-06
Hi - and welcome to the forums!

I would recommend installing a package called "firestarter'.  It allows you to configure and observe what is happening with your firewall/ports.  It's how I got Apache working.  Hope it helps!

---

### Post by stump138 on 2008-01-06
if you can access the computer from across your own network, then it is up and running properly.  You should start with your router and make sure that it is forwarding requests on port 80 to your server.

To test this, forward a request to your server through a proxy server, as trying to access your router's external IP address from inside will definitely cause you a timeout:)

---

### Post by galdren on 2008-01-06
Hi, it seems to work now..

I just turned off DMZ (this option forwards all ports to my server) and manually forwarded port 80.

Strange, I think it's a bug in the router. Anyway, thanks for your reply.

Btw, DMZ didn't even work from outside the lan. (I didn't enter the external ip of the router from within the network, I asked someone over chat to enter my external ip).

---

### Post by deci on 2008-06-14
I have the same problem ...
I set up a LAMP server and it's working fine but when I try to enter it with my external ip it seems like my router thinks I want to access the admin panel of my router
I already used the DMZ function and it's working fine as well
I can access the server from outside for gameserver, voiceserver, ftpserver, ircbouncer, ...
So how can I fix this problem that I can also access my apache ?

btw I installed firestarter with apt-get install but how can I use it ?
I don't seem to find it in my accessoires

---

