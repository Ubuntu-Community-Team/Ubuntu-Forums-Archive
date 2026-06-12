---
title: "port question"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-10-05
is linux blocking ports lower thab 1024?

---

### Post by enigma_0Z on 2006-10-05
That depends, not usually, but a firewall can be configured to do so. Do you have a firewall running? If unsure, open a console and type

```

sudo iptables -L

```

If your output is different from

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

then you have a firewall.

---

### Post by mendingo84 on 2006-10-05
thanks, i checked and i don't have a firewall...but still, i can't acces my yahoo.com account from thunderbird using mozilla's webmail extension as it makes me set a higher than 1024 port for the POP server to run...what can i do?

---

### Post by enigma_0Z on 2006-10-06
You've tried letting it set whatever it wants and it doesn't work? Most mail clients know how to access the various accounts (yahoo, hotmail, etc) and they don't use the standard POP authentication.

---

### Post by jd65pl on 2006-10-06
In ubuntu there is a kernel level firewall pre-installed and running, it is called [iptables]("http://www.netfilter.org/projects/iptables/index.html"). You could download a GUI to configure this firewall if you are used to this sort of interaction. I have found firestarter to be the best (available in the repositories)

If you wish to check which ports are open may I suggest downloading [nmap]("http://insecure.org/nmap/") from the repositories.

---

### Post by AmandaKerik on 2007-02-01
> **mendingo84 said:**
> thanks, i checked and i don't have a firewall...but still, i can't acces my yahoo.com account from thunderbird using mozilla's webmail extension as it makes me set a higher than 1024 port for the POP server to run...what can i do?

I don't see why the ports won't work if they're a high number... mine are set to 1111 and 1112 and they work fine in webmail.

I can walk you through it if you want...
PM me if you're interested,
Amanda

---

