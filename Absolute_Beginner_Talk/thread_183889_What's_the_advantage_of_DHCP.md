---
title: "What's the advantage of DHCP?"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-28
what is all of the fuzz about DHCP?  what is wrong with static ip addresses?

---

### Post by CitizenKane on 2006-05-28
Well, the ability to able to take a computer to some random network, connect to it, and automatically get an IP adress is very nice.  Most computer users do not even know what an IP address is, and if they have a static IP now they need to configure it.
And even if they configure it, they may ending choosing the same IP address as someone else, resulting in the dreaded IP conflict.

So what advantages does DHCP have over static IPs?  Just about everything.

Computers are not here to create more work for us, they are here to deal with work we don't want.  This being said, DHCP all the way.

---

### Post by user1397 on 2006-05-28
[quote=CitizenKane]Well, the ability to able to take a computer to some random network, connect to it, and automatically get an IP adress is very nice.  Most computer users do not even know what an IP address is, and if they have a static IP now they need to configure it.
And even if they configure it, they may ending choosing the same IP address as someone else, resulting in the dreaded IP conflict.

So what advantages does DHCP have over static IPs?  Just about everything.

Computers are not here to create more work for us, they are here to deal with work we don't want.  This being said, DHCP all the way.[/quote]
wow DHCP sounds great now!  except for when you use samba, because then you have to tell your pc to connect to the new ip address of your ubuntu box everytime, since DHCP changes the ip addresses every now and then

---

### Post by IYY on 2006-05-29
What I use is "static DHCP". Most modern routers support this feature. Basically, it means that the machine gets its IP through DHCP, but the IP is always the same (as configured in the router's settings). I believe this is the ultimate solution.

---

