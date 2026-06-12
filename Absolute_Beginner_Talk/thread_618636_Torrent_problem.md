---
title: "Torrent problem"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Ramrod_The_Wizard on 2007-11-20
When I run Azureus I am constantly notified that I'm firewalled on the specified port.  I have input the commands for port forwarding (changing what was necessary) and configured firestarter to allow bittorent incoming access through the port.  

I thought it was not too much of a problem for awhile, seemed to be getting passable speeds depending on what I download, but recently I havent been able to get this current download over 1 kb/s.  What is going on?  Are the ports open and Azureus can't detect it or is it a bad file?

---

### Post by MegaJim on 2007-11-20
Are you connecting through a router or directly to the Internet?  Which ports are you using to connect and listen?  6881-6889 are throttled fairly heavily nowadays, its best to choose a random block of 20 between 50k and 60k

---

### Post by alwiap on 2007-11-20
> **MegaJim said:**
> Are you connecting through a router or directly to the Internet?  Which ports are you using to connect and listen?  6881-6889 are throttled fairly heavily nowadays, its best to choose a random block of 20 between 50k and 60k

I did this when I was experiencing similar problems with KTorrent about a month ago, and have had no problems since, so I would vouch for trying this.  :)

---

### Post by Ramrod_The_Wizard on 2007-11-20
Thanks, that was exactly my problem.  I feel a little silly about it :P.

---

### Post by Ramrod_The_Wizard on 2007-11-20
A second question, why does Azureus still claim that the port is firewalled? 
The speed kicked up, but quickly dropped though that is most likely a bad seed.

---

### Post by markharding557 on 2007-11-20
test it with firewall off you will know if its your firewall then

---

### Post by Ramrod_The_Wizard on 2007-11-20
Doesn't seem to be the firewall, well that reassures me that the rules for firestarter work. : D
It doesn't seem to be anything mechanical, I guess the seeds are just very poor. Thanks for all the help!

---

### Post by MegaJim on 2007-11-20
If you are connecting through a Router, the ports you've chosen will need to be forwarded to your computer or only outgoing connections will be established.  Azureus's firewall error is probably triggered by a remote connection attempt which fails as the router drops the packet.

---

