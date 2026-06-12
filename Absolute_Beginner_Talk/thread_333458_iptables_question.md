---
title: "iptables question"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-01-07
My samba has quit working.  It was doing fine for a day or two, and then one day I booted up and it had quit working.  I have played with my smb.conf file for several versions and can't get it to even see the windows network anymore.  I'm thinking something else must be wrong, so I'm trying to troubleshoot other items.

When I do "sudo iptables -L" i get this output.

> Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


Is this a normal output?

---

### Post by steve.horsley on 2007-01-07
That is indeed the normal output, and it is the default accept everything. iptables is not blocking any packets.

If you install Wireshark Ethereal (the name changed between Dapper and Edgy), you will find it under Internet in the menu. Run it as root, it can watch what's happening across the network interface, and may give you a clue what's happening even if you don't understand the details of the protocols.

---

