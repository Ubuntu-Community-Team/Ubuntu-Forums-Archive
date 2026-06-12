---
title: "moblock blocking everything!!"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by waggingwabbit on 2008-04-21
I followed instructions from other sources already. when i first installed moblock i couldnt connect to any websites or use pidgin (and probably everything else internet related). 

i went to /etc/moblock/moblock.conf and did WHITE_TCP_OUT="80 443" at the appopriate place and then restarted moblock with moblock-control restart. but i still can't connect to any websites or anything...

any advice?

---

### Post by nicedude on 2008-04-21
Uninstall moblock and go to sourceforge and get ipblock - they have precompiled ubuntu deb install packages. It is almost exactly like peerguardian2. I installed it and it and it works great and looks great too.

---

### Post by jre on 2008-04-30
Can you post your iptables rules (e.g. with the command "moblock-control status").
Probably you also need to whitelist your router/LAN.
Something like
WHITE_IP_IN="192.168.178.0/24"
WHITE_IP_OUT="192.168.178.0/24"

Of course you have to use your LAN's IP range instead.

---

