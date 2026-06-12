---
title: "broadcast ping response"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by mckemie on 2006-12-06
How do I get Ubuntu (Edgy) to respond to broadcast pings?  Such as:
ping -bn n.n.n.0

---

### Post by steve.horsley on 2006-12-06
I don't know. 
But a broadcast ping would be n.n.n.255 (depending on the subnet mask), not n.n.n.0.

---

### Post by mckemie on 2006-12-06
> **steve.horsley said:**
> I don't know. 
But a broadcast ping would be n.n.n.255 (depending on the subnet mask), not n.n.n.0.

Well, that's interesting.  But not very informative.

My local net is 192.168.110.x; since your comment, I notice I get the same responses whether I:
ping -bn 192.168.110.0
or
ping -bn 192.168.110.255

In /etc/hosts, I have "lan" defined to be 192.168.110.0 and whenever I need to see what is working and what isn't, I "ping -bn lan".  Since I've started installing Ubuntus, I get responses only from my older boxes.

---

### Post by mckemie on 2006-12-25
Partially answering my own question:
echo "0" > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

I would still like to find the place to change so Edgy will respond to broadcast pings after boot; the above fix will go away on reboot.

OH!  I think I had to change the permissions on the above proc file to write by all.  I run it as root.

---

