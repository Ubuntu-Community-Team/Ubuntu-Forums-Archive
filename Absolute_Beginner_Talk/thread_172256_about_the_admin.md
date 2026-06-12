---
title: "about the admin"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by Jinjiruks on 2006-05-08
i just want to know if the admin can detect or monitor the websites visited by each workstations in an office setting..

---

### Post by mips on 2006-05-08
yes. easiest way is to use a proxy server (squid) that requires a user to login and then you can log all their surfing habits. without the proxy server they cannot access the web.

---

### Post by Jinjiruks on 2006-05-08
thanks.. does that mean they can also monitor anything the workstation have downloaded including plugins etc..

---

### Post by mips on 2006-05-09
You don't say whether they are win or linux machine. You would have to use some amangement tools to check installed applications/plugins.

---

### Post by Kvark on 2006-05-09
If they have installed remote monitoring softare on the workstations then they can see **everything** that is done on the workstations if they want to.

If the workstations are clean then they can't see what happens on them. But they can still have traffic monitoring software on the network servers that sees **everything** in all non-encrypted traffic that passes through their local network and internet connection. If they see unexpected encrypted traffic from a workstation then they won't know whats in the traffic but they might wonder what the user at that workstation is hiding.

But most likely they don't care enough to keep an eye on their workstations and network. At the most I'd guess they keep traffic logs of which workstation connected to what internet servers and only look at the logs if something happens that requires an investigation.

---

