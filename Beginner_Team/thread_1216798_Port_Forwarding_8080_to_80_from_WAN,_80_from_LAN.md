---
title: "Port Forwarding: 8080 to 80 from WAN, 80 from LAN"
date: 2009-07-18
forum: Beginner Team
---

### Post by Desert69 on 2009-07-18
Hi there, first time in here.
I have XAMPP installed on mi Ubuntu 9.04, with Apache listenning at port 80 (default) and I want some friends to see my webs through the Internet. The simpliest answer is: tell them to visit [http://yourip/](http://yourip/) and that's it.

The problem is that i'm behind a Zyxel Prestige 660R-61C router, so I have to do port forwarding.

In it's NAT section (under "SUA Only"), the router let's me set a port range to be redirected to a determined IP. So, telling it to forward port 80 to my LAN IP would be enough, except that port 80 at the router is being used to display the web interface.

So, my new idea: using port 8080 from the wan. I set the router to forward port 8080 to my lan address, but I don't want Apache to listen at port 8080 (don't want to use :8080 locally).

So, **how can I locally forward my incoming 8080 requests to my 80 port**?

I've never used iptables, I tried some command I found on the net ( "sudo iptables -t nat -I PREROUTING -p tcp --dport 8080 -j REDIRECT --to-port 80" ), but not worked - or, at least, it don't seems to work.

I've installed Firestarter, and set some rules:
```
At INCOMING:
Allow service  |  Port  |  User
HTTP  | 80  | everyone
HTTP-alt  |  8080  | everyone

Forward service  |  Firewall port  |  To  |  Port
Http-alt  |  8080  |  localhost  |  80
```
(actually, my firestarter is in Spanish, so the translations could not be accurate at all)

y Applied changes, and it still doesn't work.

What shall I do?

Thanks for reading, in advance..

EDIT: attached a nice picture to ilustrate what I want :) (yeah, I have to learn how to use GIMP too :D)

---

### Post by dlmarti on 2009-07-19
have your tried ssh as a short term fix?

My thought was it could be used to debug the firewall and routing stuff.

Also don't forget wireshark to find out whats going on.

---

### Post by Desert69 on 2009-07-19
mmm... not really...

but it wasn't actually the idea...

it's just about forwarding my port 8080 income traffic to my port 80...


and, yeap... i'll try with wireshark to see what happens...

---

### Post by Desert69 on 2009-07-25
well, i set apache to listen at port 8080, so there's no trouble with the router's http server, and i can connect to [http://localhost:8080](http://localhost:8080), but still can't connect with [http://my_routers_ip:8080](http://my_routers_ip:8080), so there's a problem with my router forwarding ports... i'll try with some wired not-used ports, maybe...

and i still don't know how to forward my ports locally, so there are 2 things i don't know, so far...

---

### Post by Desert69 on 2010-02-27
updating after so much time...


i think the problem was with the router's forwarding options... i think that 'router' couldn't really route...

two months ago i bought a linksys WRT54G2 router, and i configured it to forward port 8080 to my apache, and it worked...

in the midtime, i reinstalled apache (well, ok... xampp) and i think i re-installed the whole os, indeed...


but i think it was the router who wasn't really forwarding...


see ya, and thanks for the help!

---

