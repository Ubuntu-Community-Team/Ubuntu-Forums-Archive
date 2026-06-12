---
title: "opening ports"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Oddjob74 on 2007-03-27
I am trying to use Azureus. However everytime I try to load a torrent it is rejected! And a warning pop up has displayed in the bottom right of my screen asking me to open port 17064 UDP required for decentralised tracking if I have a router/firewall,  Presumably for Azureus. I am using a wireless netgear router, and no firewall that I am aware of! Could someone pls give me a walk thro!

---

### Post by savastux on 2007-03-27
It should be your netgear box. Not saying that there is a firewall set there, but you should check if you have a forward set to this port (17064) and the protocol UDP. Configure it to forward to your IP address (most probably you'll need to use a fixed IP address).

Then every request on this port, using this protocol, will be forwarded to you machine (Linux) and azureus won't complain anymore.


Sorry if I can't give you a detailed how to, but I dont have a netgear router.
I did this with my Linksys and everything work out fine!



[]'s
Savastux

---

### Post by PurplePenguin on 2007-03-27
Aren't ports like this closed by default on Ubuntu?  Maybe Oddjob74 should install something like Firestarter in order to make sure that the firewall isn't in the way, and also make sure that the router is forwarding the ports correctly (as you mentioned).

Here's a [link to portforward.com]("http://www.portforward.com/english/routers/port_forwarding/routerindex.htm")... just find the model number of your router, click on it, then select Azureus out of the list.  It'll give step by step instructions for opening ports.

---

### Post by PurplePenguin on 2007-03-27
[Just found a link]("http://justanothertechblog.blogspot.com/2007/01/azureus-and-ubuntu.html") to poking some holes in Ubuntu in order to get Azureus to work.  Looks like some simple step by step instructions.

---

### Post by Oddjob74 on 2007-03-27
Cheers guys, I'll have a play!:)

---

