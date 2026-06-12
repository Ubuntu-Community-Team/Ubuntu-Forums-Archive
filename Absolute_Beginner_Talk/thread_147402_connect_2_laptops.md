---
title: "connect 2 laptops"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by firehead on 2006-03-20
hi all
i'd like to connect my laptop (running breezy) with a powerbook (running osX). now is this possible?
and if so, could anyone please give me a detailed howto please?
i know i could either use a crossover-cable or a switch to connect 2 machines, which of them is better (in terms of easy-to-useness and speed)?
thx in advance

---

### Post by Sendervictorius on 2006-03-20
No detailed howto here, but I can tell you how it is done.

Either crossover-cable or a ethernet hub/switch/router is ok. Depends on whether you want to be able to plug in more into your network, such as broadband modems, etc later.

Once you have them connected physically, the ethernet part should work fine. The next step is to get the two machines talking tcp/ip to each other. That requires setting ip addresses on each port, and having each pc know about the other.  You would open up your network configuration programs on the respective machines (System > Administration > Networking on Ubuntu) and set your ip addresses to (say) 192.168.0.10 and 192.168.0.11. 

If you want each machine to know the other by name, you will need edit the /etc/hosts file, and associate the name with the ip address.

At this stage you should be able to run the 'ping" command from each machine and ping the other machine.

Finally, you need to run applications to talk to the other system. Software such as vnc will allow one machine to "remote control" the other. ssh, on the other hand will allow one pc user to "log in" to the other as a new user. You could run a web server on one pc, and a browser on the other, you can share file systems... the world is your oyster!

If you want to extend your network, and have one pc acting as a gateway to the internet, or somesuch you will need to get a bit fancier with the configuration.

---

### Post by OffHand on 2006-03-20
[QUOTE=firehead]hi all
i'd like to connect my laptop (running breezy) with a powerbook (running osX). now is this possible?
and if so, could anyone please give me a detailed howto please?
i know i could either use a crossover-cable or a switch to connect 2 machines, which of them is better (in terms of easy-to-useness and speed)?
thx in advance[/QUOTE]Yes, this is possible. You need either a crosscable and plug it into the second ethernetcard of the machine that's connected to the internet or a normal cable if you use a router. In OS X you gotta open the ports in the firewall for ftp or ssh or whatever. Then approach it with ftp or connect to server.

---

### Post by firehead on 2006-03-20
thx guys
i'll give it a try and ask further questions if in need ;-)

---

