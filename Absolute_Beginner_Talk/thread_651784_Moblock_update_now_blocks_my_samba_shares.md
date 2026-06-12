---
title: "Moblock update now blocks my samba shares"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by uknowho008 on 2007-12-27
it worked fine until the latest update. now when i go to network places and click on windows network nothing comes up until i stop moblock. how can i fix this? should i just white list the port? if so what ports? or is it blocking my private network? i dont understand why its doing this suddenly.

i also cant ssh or ping any of my servers anymore while moblock is running. everything is behind a router and in a private network. 192.168.1.*

---

### Post by uknowho008 on 2007-12-28
updated my post.

---

### Post by jre on 2007-12-28
> **uknowho008 said:**
> it worked fine until the latest update. now when i go to network places and click on windows network nothing comes up until i stop moblock. how can i fix this? should i just white list the port? if so what ports? or is it blocking my private network? i dont understand why its doing this suddenly.

i also cant ssh or ping any of my servers anymore while moblock is running. everything is behind a router and in a private network. 192.168.1.*
Yes, your LAN is blocked because I changed the default blocklists because of another bug.
Simply edit /etc/moblock/moblock.conf:
```
WHITE_IP_IN="192.168.1.0/24"
WHITE_IP_OUT="192.168.1.0/24"
```
and do a "moblock-control restart" afterwards

---

