---
title: "IPTables Nasty Surprise"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by perfecttao on 2008-02-29
Ok, so I've been using Ubuntu for a little while now, and also use Fedora.  I work managing a mixed MS/Linux environment, and would consider myself pretty security aware....

I've just been messing around with pen testing on my firewall at home, and have effectively positioned myself just outside the firewall on my network.  As a result of this, by chance I decided to check what my IPtables rules were - this is the first time this machine has been out "in the wild" away from the protection of our corporate firewall.  I couldn't believe it when I found out that by default the IPTables rules are set to effectively "permit all" by default.  This is pretty scary as I can imagine a large number of users assuming Linux is "more secure" than Windows (as the general consensus on this forum states) without realising that their shiny new Ubuntu install is only POTENTIALLY more secure than  windows - it's like having a fantastic home security system, first class locks on the windows and leaving the door open....

Surely the out-of-the box install should allow for outbound HTTP/S only.  As additional services are required, clear instructions should be provided on how to open ports.  Firestarter is extremely user friendly!

---

### Post by PeterJS on 2008-02-29
Firewalls are not meant to provide outbound security, by the time you've gotten to that point your system is already compromised and your point of failure was somewhere else. The default rules make prefect sense, there are none, because there is nothing to protect, all out bound connections are authorized (or should be)* and there are no listening ports to make inbound connections to.

*If this isn't the case go back and see the first sentence, you've got bigger problems

---

### Post by perfecttao on 2008-02-29
Fair point about the bigger problems - and I can see where you are coming from on an out of the box install.  However, as networkable modules get added (Samba/NFS etc) will most users know/remember that they have to secure these ports?  From my perspective it's better that users have a learning curve as they try to troubleshoot an issue like samba not working than to suffer compromised data - or worse!

With regard to the outbound ports - Just my thoughts coming from a windows environment, where innocent looking applications are often nefarious, and my hyper paranoid nature wants to know what my machine is doing and when.....

---

