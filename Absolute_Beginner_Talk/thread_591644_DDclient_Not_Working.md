---
title: "DDclient Not Working"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-10-25
Hey guys. Today, I installed the DDclient on my machine. For about five minutes, my new host name worked fine, and then it stopped. About an hour later, I restarted the client. Still nothing. What can I do to make this work? Thanks.

---

### Post by p_quarles on 2007-10-27
I'm not sure exactly what you mean when you say it worked for five minutes. How many times did your IP address change in that amount of time?

Anyway, could you say which DNS service you are trying to use ddclient with? Many of them have customized configuration files that you need to setup before ddclient works. In my experience, the default configuration never works.

---

### Post by bsh on 2007-10-30
yeah, i just installed it about a month ago and thought it works, since could reach my pc using the hostname.
but then i watched some logs and it turned out, ddclient doesn't work.
the reason i could reach my pc was that, i put my wan ip on the dyndns website, and my ip didn't change since then. but ddclient didn't update my ip on members.dyndns.com at all.
i found the way to solve this.
first, the log stated, it could not reach "members.dyndns.com" which is the default server i think. i changed this in the config to try "members.dyndns.ORG" and it worked then. (obvjously ddclient had to be restarted"
then, it updated the ip with my local ip address, which is wrong, since i'm behind a router.
i modified the line in the config
from:
"use=if, if=eth0"
to:
"use=web"
and it works now.

---

