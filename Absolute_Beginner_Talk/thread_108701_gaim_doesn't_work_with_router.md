---
title: "gaim doesn't work with router"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by zasf on 2005-12-26
Hi all,

It's been a month that I use ubuntu, new to linux, still windows user at work, I enjoy this wonderful OS. I'm now running most of what i need: wired and wireless network, 56k modem, win/mac file sharing, but..

Gaim won't connect when I'm at home.. it works with the 56k modem but not with my router, what should i do? forward any ports? wich ones? I wasn't able to find any help on gaim sourgeforge page.

Thank you

---

### Post by akniss on 2005-12-26
Which router do you have?  Does it have a hardware firewall?  Do you use a software firewall like firestarter?  Any more information you can give us?

---

### Post by zasf on 2005-12-27
> Which router do you have?

D-Link DSL-G604T

> Does it have a hardware firewall?

Yes, it blocks all ports inbound. I do forward ports but for software like emule that need to listen on a port for incoming traffic. In my opinion, gaim doesn't have to listen but only to "connect".

> Do you use a software firewall like firestarter?

Since i'm behind the routers firewall, i didn't configure any firewall software in ubuntu. Should I open some ports to let gaim have outbound traffic??

> Any more information you can give us?

Yahoo! Messenger works, but I think it uses http, Gaim works when connected with modem.. Gaim worked at the very first install, when I rebooted It stoped working.

If you need to know anything else, please ask :)

---

### Post by BoyOfDestiny on 2005-12-27
[QUOTE=zasf]D-Link DSL-G604T



Yes, it blocks all ports inbound. I do forward ports but for software like emule that need to listen on a port for incoming traffic. In my opinion, gaim doesn't have to listen but only to "connect".

Since i'm behind the routers firewall, i didn't configure any firewall software in ubuntu. Should I open some ports to let gaim have outbound traffic??



Yahoo! Messenger works, but I think it uses http, Gaim works when connected with modem.. Gaim worked at the very first install, when I rebooted It stoped working.

If you need to know anything else, please ask :)[/QUOTE]

Strange that it worked once... 
Anyway, try port 5190 (I'm pretty sure that's the port aim/oscar uses)

---

### Post by zasf on 2005-12-27
[QUOTE=BoyOfDestiny]Strange that it worked once... 
Anyway, try port 5190 (I'm pretty sure that's the port aim/oscar uses)[/QUOTE]

How do I know if ubuntu blocks outbound traffic on port 5190? router shouldn't..

---

### Post by zasf on 2005-12-27
[QUOTE=BoyOfDestiny]Strange that it worked once... 
Anyway, try port 5190 (I'm pretty sure that's the port aim/oscar uses)[/QUOTE]

the point is that I mainly use yahoo messenger, anyone knows which port uses??

---

### Post by fordfan753 on 2005-12-27
[QUOTE=zasf]the point is that I mainly use yahoo messenger, anyone knows which port uses??[/QUOTE]

Yahoo: 5050 (I think)
MSN: 1863

---

### Post by zasf on 2005-12-28
still same problem.. no solution yet. I installed firestarter, everything seems to be ok

Outbound traffic policy: permissive by default, blacklist traffic

Anyone can help?

---

### Post by zasf on 2006-02-26
[QUOTE=zasf]still same problem.. no solution yet. I installed firestarter, everything seems to be ok

Outbound traffic policy: permissive by default, blacklist traffic

Anyone can help?[/QUOTE]

I added my ISP's DNS servers on /etc/resolv.conf togher with router's IP, it seems that my router doesn't work properly as DNS server for some programs.. it's a workaround but it works.

---

