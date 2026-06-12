---
title: "Network Topology - Can This Work?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-03-31
Hi,

The unsinkable Molly Brown is still at it ... I've decided ultimately to resign my Windows 2K ICS box and replace it with a Ubuntu-based proxy server (gee, I *hope* I'm getting all these terms right!), as well as create a data server (MySQL) and perhaps even a mail and **Intranet** web server, although that might be asking for trouble all on this same proxy server box.

Now, here is the current state of my little LAN:

[IMG]http://www.tightbytes.com/images/Home_Network2.jpg[/IMG]

As you can see, the Win2K box is kinda in control, since it's the connection to the Internet. In order to do ICS, it assigns IP addresses via dhcp, even to the Ubuntu Server. My Question: is it possible to give the server its own static IP address and, on this same physical network, have the other WinXP/Ubuntu boxes be able to connect to it and use NFS and *still* be able to be connected to the Internet via the Win2K box? I know this must sound like a totally moronic question and it's not a show-stopper if I can't do it. I'm going to eventually replace the Win2K box with the Ubuntu server, but I'd like to configure the Ubuntu server first and get everything working properly, or is that unrealistic, given its current location in the LAN vs its projected location?

What I hope to do with the Ubuntu box is:
1. - set up a proxy-server / software router / firewall / NAT sort-of-thing
2. - learn command-line server stuff, as in: get really comfortable with it
3. - test my php/MySQL-based website (TightBytes.com) locally before uploading the site database
4. - have fun and get to know all of you brilliant people a lot better, because I'll have a squillion questions :) 

Fortunately, at this point I'm not setting up a production server - I can play all I want without the pressure of a boss who wants this server up and running in x-number of hours... ](*,) 

Anyway, looking forward to hearing from ya, and hope y'all have a good weekend back there in the States (we're in the next day down here in Oz... :)  )

Cheers,
Robyn

---

### Post by Robynsveil on 2007-03-31
...and before anyone can even reply, just wanted to add - this is where I ultimately hope to be with this LAN six months from now:

[IMG]http://www.tightbytes.com/images/Home_Network3.jpg[/IMG]

... not sure about whether I want the proxy server to be running Samba, necessarily - the XP-only machines will still be able to connect to the Internet via the proxy server without Samba installed on the proxy server, right?

---

### Post by lamalex on 2007-03-31
yeah that should work, have fun!

---

### Post by Austin_KW on 2007-03-31
You should have no problem doing this. firestarter lets you share you internet connetion like windows ICS with a graphical interface and easy setup. You could also install a proxy like privoxy and a http caching server like squid. 

There are also lightweight linux server solutions that could turn your 2k box into a router/server/web server or design your own, no end of possibilities.

---

### Post by arron on 2007-03-31
Yes you can make the nfs server dynamic, but you will need some form of name resolution.  I believe under samba it will find the shares by name with time, but for nfs it will need a name it can resolve.  You can have dhcp assign a static ip to the server.

But usually it is always best to have any main servers with a static ip, then any trouble shooting is made a lot easier and less time configuring tricky applications.

For the firewall as mentioned firestarter is awesome to get up and running.  It does most normal things a user needs.  For anything getting more complicated i would recommend  arno-iptables-firewall (what i use) or shorewall.

---

### Post by Robynsveil on 2007-03-31
Thanks to Lamalex, Austin and Arron for their responses...

> **arron said:**
> Yes you can make the nfs server dynamic, but you will need some form of name resolution.  I believe under samba it will find the shares by name with time, but for nfs it will need a name it can resolve.  You can have dhcp assign a static ip to the server.

I'm going to assume that you are referring to the current layout... when you say "You can have dhcp assign a static ip to the server", are you talking about the dhcp component in ICS? I didn't think Win2K's ICS let you have any control over what IP addresses to assign the other machines: it just higglety-pigglety assigns random numbers in the 'x' of 192.168.0.x as they come online. 

> **arron said:**
> But usually it is always best to have any main servers with a static ip, then any trouble shooting is made a lot easier and less time configuring tricky applications.

So, in the *current* configuration, I could conceiveably assign the server box hanging off the second switch (they're switches, not hubs) a static IP address and have one of the other Ubuntu boxes be able to access this box with NFS *if* I assign a static IP address to them. However, that box would lose connection to the internet since dhcp (ICS) wouldn't recognize that box... or I could just connect with Samba, right?

> **arron said:**
> For the firewall as mentioned firestarter is awesome to get up and running.  It does most normal things a user needs.  For anything getting more complicated i would recommend  arno-iptables-firewall (what i use) or shorewall.
One of the challenges I face is that my WinXP users run MSN Messenger, which requires specific open ports, as well as some peer-to-peer software which requires configuring as well - is FireStarter up to that, or should I be looking at the more industrial-strength firewalls you mentioned? I also want to be able to have better control over usage and how much these programs (the peer-to-peer stuff) is able to run.

---

### Post by Austin_KW on 2007-03-31
Firestarter will allow you to add rules to configure port forwarding, service ports, allowed addresses etc like on a simple consumer router. If you want to get really advanced you may have to manually configure IP tables or try one of the others.

I suggest that you install firestarter and have a play with it to start with. With firestarter it is very simple to get an ICS type router up and running. I dont know the other firewalls so I cant say if they allow you to configure traffic shaping and policing. I have seen tutorials on the "tc" command but I dont remember anything to do traffic control from a GUI (but is is not something I have looked into)

---

