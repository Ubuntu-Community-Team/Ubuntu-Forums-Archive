---
title: "amule configuration"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by dboss on 2007-02-13
Hi everyone,

I'm new to Ubuntu and would like to know how to configure Amule p2p program in Ubuntu

Thx

---

### Post by daou on 2007-02-13
Just install it from synaptic.

You probably need to open some ports on your firewall. If you don't know how to edit your iptables, I suggest you get firestarter (also available in Synaptic).

By default, you need to open these ports in firestarter:

# 4662 TCP (outgoing and incoming): Client to client transfers.
# 4665 UDP (outgoing and incoming): Used for global server searches and global source queries. This is always Client TCP port + 3
# 4672 UDP (outgoing and incoming): Extended eMule protocol, Queue Rating, File Reask Ping, Kad. Kad will be 'firewalled' if NAT (Network Address Translation) remaps this port number. 

If your ISP/other entity blocks these ports, you can change them in aMule settings. Then just allow those ports instead.

---

### Post by dboss on 2007-02-13
Thx

---

