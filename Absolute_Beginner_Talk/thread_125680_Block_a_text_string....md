---
title: "Block a text string..."
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by nixclusive on 2006-02-04
Is there a way to explicitly define a text string to be blocked out of outbound traffic? I have a firewall up and running but I couldn't find that.

---

### Post by cwaldbieser on 2006-02-04
[QUOTE=nixclusive]Is there a way to explicitly define a text string to be blocked out of outbound traffic? I have a firewall up and running but I couldn't find that.[/QUOTE]
You can use the iptables string match, but it matches a string ANYWHERE in the packet, so it is usually way too general for most filtering operations.  It can be used in conjunction with something like the QUEUE target, so you can identify suspected packets and then pass them to a user-space program to inspect the payload more thoroughly.

If you are just doing HTTP filtering, you could probably use squid.

---

