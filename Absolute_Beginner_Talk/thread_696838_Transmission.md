---
title: "Transmission"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by H3!ST on 2008-02-14
I decided to install Transmission. It works but it's slow. How do I make it download faster?

---

### Post by ashmew2 on 2008-02-15
Have you tried other torrent clients? Are they also slow ? Have you setup port forwarding to forward ports if you are behind a router ? Are you using a firewall ? Have you looked under Transmission's Preferences if your download and upload speeds are limited ? 

LOl sorry for so many questions , but couldnt help the urge :P

---

### Post by H3!ST on 2008-02-15
> **ashmew2 said:**
> Have you tried other torrent clients? Are they also slow ? Have you setup port forwarding to forward ports if you are behind a router ? Are you using a firewall ? Have you looked under Transmission's Preferences if your download and upload speeds are limited ? 

LOl sorry for so many questions , but couldnt help the urge :P

Yeah, I tried uTorrent but couldn't get the ports to forward because every time I opened it only the icon on the task bar would show. I tried clicking the hide/show button but it did nothing so I downloaded Transmission instead. I'm also not sure if I forwarded the ports on Transmission because I don't know how to do it. I think I'm using a firewall, I was told to download Firestarter but I don't really know how to use it.

---

### Post by ashmew2 on 2008-02-15
Get this great Utility called Testport to check whether the desired port is forwarded properly.
[http://www.voipuser.org/port_forward_tester.html](http://www.voipuser.org/port_forward_tester.html)

Also , if you are behind a router , you need to first setup port forwarding on the router first and then tell your programs to use the open ports for faster connectivity.

To tell Transmission which port to use (port should be forwarded) , open it and go to 
File > Preferences . Check the Listening port.

---

