---
title: "VNC, ports and firewall problem"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by Villenya on 2005-09-13
I just set up a VNC server using the vncserver command. It works fine when i use my LAN ip address (192.168.*.*). But when i use my WAN ip it say connection is refused, same thing happens when i try to go through port 5800 for the java applet. I already forwarded port 5800-6000 but it still refuse my connection?  im guessing there is a firewall by default for ubuntu??  any one got an idea?

---

### Post by heimo on 2005-09-13
Check with this command which tcp port your vncserver is listening on:
 ```
 netstat -ltpn
``` 

At least for me it was >6000. Do not forward any additional ports and if possible, accept connections only from certain ip-addresses.

---

