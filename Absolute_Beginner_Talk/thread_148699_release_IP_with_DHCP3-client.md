---
title: "release IP with DHCP3-client"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by cotcot on 2006-03-22
Is there anybody who knows how to release the IP (dynamic; cable) with DHCP3-client ? I could not find a man page.

Alernatively I could install DHCPCD instead of DHCP3-client. Then I know how : sudo dhcpcd -k eth0. Any comments on this idea ?

Thanks

---

### Post by dragonfyre13 on 2006-03-22
take a look at 

ifconfig --help

or

man ifconfig

if that fails. there should be something like "ifconfig -release" though perhaps I'm remembering it from somewhere else.

---

### Post by dcstar on 2006-03-23
[QUOTE=cotcot]Is there anybody who knows how to release the IP (dynamic; cable) with DHCP3-client ? I could not find a man page.

Alernatively I could install DHCPCD instead of DHCP3-client. Then I know how : sudo dhcpcd -k eth0. Any comments on this idea ?

Thanks[/QUOTE]
sudo dhclient -r

---

### Post by cotcot on 2006-03-26
Both suggestions did not work. I deinstalled dhcp3-client and installed dhcpcd. I can now release the IP with sudo dhcpcd -k eth0.
Thanks anyway for your suggestions. Once again I learned something.

---

### Post by dragonfyre13 on 2006-03-27
np, sorry niether worked. At least it is fixed.

---

