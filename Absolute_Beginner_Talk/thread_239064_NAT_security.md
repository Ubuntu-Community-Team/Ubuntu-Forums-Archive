---
title: "NAT security"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by tjb891 on 2006-08-18
I have a NAT router and I want to open a port for use with bittorent. Is this safe to do in Ubuntu since I see no option to use a firewall?

---

### Post by kebes on 2006-08-18
Ubuntu (linux) out of the box has no open ports, so it is secure by default. The linux firewall (iptables) is essentially built right into the kernel.

Opening up one port on your router for bit-torrent is perfectly fine. You will be safe. I wouldn't worry about it.

If you want to be able to easily edit your firewall rules, you can install the "firestarter" interface.

---

