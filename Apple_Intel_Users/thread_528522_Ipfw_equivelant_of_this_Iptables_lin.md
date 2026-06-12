---
title: "Ipfw equivelant of this Iptables lin"
date: 2007-08-18
forum: Apple Intel Users
---

### Post by thetinguy on 2007-08-18
Hi. I know this is a little ot but I have this line in my iptables on my pc. I was wondering if anyone could tell me what the equivalent  of this line is in ipfw. Here is the line:

iptables -A INPUT -p tcp –dport $TORRENT_CLIENT_PORT –tcp-flags RST RST -j DROP

It's a fix so comcast doesn't screw up seeding my torrents.

Help is very appreciated! Thanks! ):P

---

