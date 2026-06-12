---
title: "Setup a router - help"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by penbrock on 2006-08-19
I have had a Debian box running my web/e-mail server for years now. It is now time for me to try to replace my Netopia router and what better to use then Linux. Well being new I have a lot of questions.

Here is what I need/want in the end;
1) Router/gateway from cable modem to a 6 computer LAN
2) Forward ports to my web server box
3) Connect and route to my office with PPTP VPN
4) Basic QoS for my IP phone
5) Squid would be nice to play with
6) file storage (Samba)
7) Serve my Cannon i560 printer to the network
8) Firewall
9) Webmin for configurations

Questions, what is the best packages to use for a newbie. I need ones that are very easy to setup. Is there an order things need to be installed? 
I have been able to get FreeSwan and Samba all running great on my Debian box using Webmin so I feel I can get those running with little trouble (I hope), Squid looks like it just runs, printer I sould be ok with using Samba, Firewall maybe easy with Webmin I would think but I have never tried.

---

### Post by kidders on 2006-09-04
That all sounds good :)

[LIST=1]
[*]**Router/gateway** - I would use iptables for this.
[*]**Forward ports** - iptables -t nat -A PREROUTING -p tcp --dport 80 ..... -j DNAT --to tar.get.ip.addr
[*]**VPN support** - FreeSwan sounds good :)
[*]**QoS** - You need to make quite a few kernel tweaks for QoS to cooperate ... but knowing Ubuntu, there all available as modules! The usual traffic shaper app is called "tc"
[*]**Squid** - Very handy. If you're running a web server, you may be interested in running it "backwards" to cache incoming requests, rather than outgoing ones. Also, transparent proxying is a doddle, if you're so inclined.
[*]**Samba** - I currently have a Windoze domain controller running Samba. It was a *real* pain in the a$$ to iron all the kinks out of it!
[*]**Printer Sharing** - CUPS + Samba sounds good
[*]**Firewall** - iptables again :) It has support for a few QoS-related things too, in case you wanted it to route your VOIP traffic differently or some such.
[*]**Webmin** - I use webmin for *some* things, but I don't really trust it. Maybe I'm just paranoid :P
[/LIST]

You seem to have all this figured out already! In terms of ease of configuration, iptables and samba aren't exactly simple ... and QoS settings can take a **lot** of tinkering, but imho you're better to go with the well-known stuff where you can. That way, if you hit a problem, half the world has seen it before.

Installation order is pretty irrelevant, I'd say.

Sounds like you're going the whole hog with your LAN, eh? The only thing missing is some multimedia stuff like maybe an iTunes server and video streaming :P

---

