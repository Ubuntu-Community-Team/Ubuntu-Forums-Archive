---
title: "Slow connection after vmserver installation"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by iopo on 2007-03-13
Hi!
I recently installed vmserver and now it works perfectly.

Anyway, I noticed that now my firefox/swiftfox is extremely slow! I checked the firewall and I noticed a Ipv6 tunnel in the active connections that wasn't there before.

I then searched the forums to see what is a ipv6 tunnel and I found this [http://www.ubuntuforums.org/showthread.php?t=87798](http://www.ubuntuforums.org/showthread.php?t=87798). Thread 8 suggests a couple of way to check weather your connection is working properly. Here are my outcomes:

andrea@andrea-laptop:~$ host [www.google.com](www.google.com)
[www.google.com](www.google.com) is an alias for [www.l.google.com](www.l.google.com).
[www.l.google.com](www.l.google.com) has address 64.233.161.99
[www.l.google.com](www.l.google.com) has address 64.233.161.147
[www.l.google.com](www.l.google.com) has address 64.233.161.104
[www.google.com](www.google.com) is an alias for [www.l.google.com](www.l.google.com).
;; connection timed out; no servers could be reached

andrea@andrea-laptop:~$ ip -6 route
fe80::/64 dev eth1  metric 256  expires 21333661sec mtu 1500 advmss 1440 hoplimit 4294967295
fe80::/64 dev vmnet1  metric 256  expires 21333661sec mtu 1500 advmss 1440 hoplimit 4294967295
fe80::/64 dev vmnet8  metric 256  expires 21333661sec mtu 1500 advmss 1440 hoplimit 4294967295
ff00::/8 dev eth1  metric 256  expires 21333661sec mtu 1500 advmss 1440 hoplimit 4294967295
ff00::/8 dev vmnet1  metric 256  expires 21333661sec mtu 1500 advmss 1440 hoplimit 4294967295
ff00::/8 dev vmnet8  metric 256  expires 21333661sec mtu 1500 advmss 1440 hoplimit 4294967295
unreachable default dev lo  proto none  metric -1  error -101 hoplimit 255


Thanks a lot!

---

