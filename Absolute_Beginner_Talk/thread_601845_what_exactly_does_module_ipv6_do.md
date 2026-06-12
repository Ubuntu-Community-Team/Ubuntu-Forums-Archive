---
title: "what exactly does module ipv6 do ?"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2007-11-03
i've recently been noticing "not loading blacklisted module ipv6" whenever i reboot, and googling for it seems to suggest it's better off disabled and blacklisted anyway, but i'm just curious to know what it actually does and why it's blacklisted ?

and will it affect my system in any way, blacklisted or not ?

cheers :)

---

### Post by Jimmyfj on 2007-11-03
IPv6 is the new version of the TCP/IP  protocol for the internet but it hasn't been fully implemented yet. IPv6 is set to replace IPv4 which is the current IP protocol on the Internet.
IPv6 makes for a larger amount of IP addresses than IPv4 but is still in development.

---

### Post by scorp123 on 2007-11-03
> **jasonwatkins said:**
> i've recently been noticing "not loading blacklisted module ipv6" whenever i reboot, and googling for it seems to suggest it's better off disabled and blacklisted anyway, but i'm just curious to know what it actually does and why it's blacklisted ?  It's blacklisted because nobody is really using IP version 6. [http://en.wikipedia.org/wiki/Ipv6](http://en.wikipedia.org/wiki/Ipv6)

The main problem is that when "ipv6" is active it slows down all the IPv4 traffic; so accessing your LAN and the Internet might all of a sudden take longer because the OS tries to send things via IPv6 ... but as I said above: Nobody is really using it yet, despite all claims that the IPv4 addresses will soon all be exhausted. So when you send stuff via IPv6 chances are you will run into a timeout, you as user will perceive the network connection being slower than usual. And then the computer will try to send all the packets again via IPv4 ... which it should have done right from start.

So to avoid this "ping pong" game between IPv6 (which nobody is using) and IPv4 (which is the present-day standard for TCP/IP networking) it's best not to allow the OS to load the "ipv6" kernel module (= device driver); hence it's "blacklisted" which means "don't load this!".

---

