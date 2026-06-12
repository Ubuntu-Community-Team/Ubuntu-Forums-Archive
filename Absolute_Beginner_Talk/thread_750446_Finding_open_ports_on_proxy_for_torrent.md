---
title: "Finding open ports on proxy for torrent"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by farueulogy on 2008-04-09
At university we have a proxy and I can't seem to torrent even though the proxy information is entered in deluge. I suspect it is because the ports I'm using are closed.

I've tried changing them and making them random but I can't find any open ports.

How do I?

Is there anything else this could be?

---

### Post by dokdoom on 2008-04-09
Do you know the public or private IP of the proxy server? If so to find open ports just:

telnet proxy.server <PortNumber>

If it is open it will tell you that you are connected. If it closed it will say Unable to connect to remote host.

---

