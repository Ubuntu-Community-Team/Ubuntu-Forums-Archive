---
title: "Should I block all ICMP"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by philinux on 2008-03-20
New router Siemens SE587 from tiscali has a rather weird config. The firewall can be either on or off, no configuration. So I used firestarter to configure iptables to block all icmp.

Did I do the right thing? Everything is working and when i check with shields up I'm completely stealthed.

---

### Post by milton1 on 2008-03-20
in most inbound cases, ICMP is useless to you and helpful to attackers. I generally block all but ICMP reply, and that I leave open so I can get responses when I ping others. Getting perfect stealth is good; it means you will be less of a target.

---

### Post by philinux on 2008-03-20
Thanks for reply. Anyone else like to chip in?

---

