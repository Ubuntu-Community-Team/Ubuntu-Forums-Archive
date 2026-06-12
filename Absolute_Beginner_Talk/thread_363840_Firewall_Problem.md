---
title: "Firewall Problem"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Ryan H on 2007-02-17
I've had aMule for a while, but it keeps saying it is firewalled, which I think it is because it takes forever to connect to the servers, and KAD is blocked completely, how do I unblock these ports from my firewall?

-Ryan H

---

### Post by Zuuswa on 2007-02-17
Is your router blicking ports as well?  This may be the case.  Also, try using something like firestarter, as it allows you to easily edit your iptables and it allows you to moniter attempted connections to your computer.

---

### Post by Ryan H on 2007-02-17
I don't think my router blocks any ports, atleast I've never had a problem with it. I just need to know the commands to unblock the ports:
```
# 661 TCP (outgoing): Port, on which a server listens for connection (defined by server).
# 4662 TCP (outgoing and incoming): Client to client transfers.
# 4665 UDP (outgoing and incoming): Used for global server searches and global source queries. This is always Client TCP port + 3
# 4672 UDP (outgoing and incoming): Extended eMule protocol, Queue Rating, File Reask Ping
# 4711 TCP: WebServer listening port.
# 4712 TCP: internal Connection port. Used to communicate aMule with other applications such as aMule WebServer or aMuleCMD.
```

In the terminal.

-Ryan H

---

