---
title: "Security measures to take in Ubuntu"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-09-25
I'm a fairly new convert from Windows, so I need some help setting up security.

Do I actually need a firewall, and what would be the worst thing which could happen without it?

Basically, what do I need to do and why?

Cheers :)

---

### Post by monktbd on 2006-09-25
if you dont install any servers (and ubuntu does not with a default install) then you dont need a firewall.

if you want one then you can use firestarter which is a front-end to the usualy iptables packetfilter firewall.

usual linux firewalls work by checking traffic over ports and not by watching applications trying to connect (like e.g. zonealarm).

---

### Post by tribaal on 2006-09-25
Actually you *already* have a firewall if you're running Ubuntu :)

"iptables" is a firewall system, and comes installed by default, with maximum security settings. You can install the "firestarter" package if you feel you need to tweak your iptables configuration. 

If you're just setting up a desktop comupter, all you need for security is a strong password (more than 8 chars long, with at least one cap, one symbol and one number) and the default setup of iptables :)

Enjoy :)

- trib'

---

