---
title: "Too much firewall?"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by camara on 2005-07-10
I guess this is a strange problem for some (or not). I installed ubuntu this week and I'm impressed with a lot of things. But my idea was to make my home desktop become the gateway using linux (ubuntu). 

It's working fine, except for one thing: it's apparently blocking my email client (Eudora in Windows) to send email... I'm using ipmasq+dnsmasq. I tried with my wife's laptop and her eudora is working fine. The difference is that my SMTP server demands SSL connection...

Any idea?

Thanks a lot in advance...

---

### Post by FLeiXiuS on 2005-07-10
$ sudo iptables -L

Paste the output.

---

### Post by camara on 2005-07-10
[QUOTE=FLeiXiuS]$ sudo iptables -L

Paste the output.[/QUOTE]
<Notice I added a line in my initial message... my client demands SSL connections>

Hi (and thanks for the quick reply!!:)))

Here goes the result of iptables:

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
LOG        all  --  127.0.0.0/8          anywhere            LOG level warning
DROP       all  --  127.0.0.0/8          anywhere
ACCEPT     all  --  anywhere             255.255.255.255
ACCEPT     all  --  192.168.1.0/24       anywhere
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4
LOG        all  --  192.168.1.0/24       anywhere            LOG level warning
DROP       all  --  192.168.1.0/24       anywhere
ACCEPT     all  --  anywhere             255.255.255.255
ACCEPT     all  --  anywhere             bl5-45-22.dsl.telepac.pt
LOG        all  --  anywhere             anywhere            LOG level warning
DROP       all  --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  192.168.1.0/24       anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTAB
LISHED
LOG        all  --  anywhere             192.168.1.0/24      LOG level warning
DROP       all  --  anywhere             192.168.1.0/24
LOG        all  --  anywhere             anywhere            LOG level warning
DROP       all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             255.255.255.255
ACCEPT     all  --  anywhere             192.168.1.0/24
ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4
LOG        all  --  anywhere             192.168.1.0/24      LOG level warning
DROP       all  --  anywhere             192.168.1.0/24
ACCEPT     all  --  anywhere             255.255.255.255
ACCEPT     all  --  bl5-45-22.dsl.telepac.pt  anywhere
LOG        all  --  anywhere             anywhere            LOG level warning
DROP       all  --  anywhere             anywhere

---

