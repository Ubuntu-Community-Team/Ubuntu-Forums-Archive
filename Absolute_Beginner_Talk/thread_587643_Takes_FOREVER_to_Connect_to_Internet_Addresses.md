---
title: "Takes FOREVER to Connect to Internet Addresses"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Bezmotivnik on 2007-10-22
OK, I blew off 7.10 on the one machine that had so many problems and installed it instead on a different test box with the same drives. Installation went fine and after some initial wierdness and reboots everything SEEMS to have straightened itself out, except for one very strange problem BOTH machines had:  Even though they were connected to the wireless network and could ping the gateway, they take absolutely unbelievably long to connect to any internet address.  The XP machines using the same AP don't have this problem.

It takes maybe two or three minutes to resolve & connect up to [www.google.com](www.google.com)...or here...or anywhere.

Any thoughts on this weird problem?  I was using Automatix to install codecs, but it would time out before resolving the sourceforge server addresses.  

Thanks for any help.

---

### Post by bubbalouie on 2007-10-23
IPV6 might need to be disabled.

1) In firefox go to **about:config** then go to the element for IPV6 (network.dns.disableIPv6 I think, presently in windows @ work having lunch) and make sure it is disabled

2) Disable IPV6 on your system, I have a link below for that:

[http://ubuntuforums.org/archive/index.php/t-87798.html](http://ubuntuforums.org/archive/index.php/t-87798.html)

Frankly I do not know why neither of these are done by default with an easy enable option, IPV6 causes all sorts of strange issues.

Good luck :)

---

### Post by Ehtetur on 2007-10-23
> **bubbalouie said:**
> IPV6 might need to be disabled.

1) In firefox go to **about:config** then go to the element for IPV6 (network.dns.disableIPv6 I think, presently in windows @ work having lunch) and make sure it is disabled


To disable ipv6 DNS lookups in firefox, network.dns.disableIPv6 should be set to true.
But since you're at lunch, we'll let that one slide.. :p

And anyways, your previous post on disabling ipv6 in Gutsy was just what I needed to get on the net!

---

### Post by Bezmotivnik on 2007-10-23
Yep, kids, that's what was wrong.

Whoever made the initial call on that config falls into the "Needs a Beatin'" category!

Thanks for the assist and mark this one "Solved"!

---

### Post by bubbalouie on 2007-10-24
No worries, glad to be of service :)

And agreed on 2nd point

---

