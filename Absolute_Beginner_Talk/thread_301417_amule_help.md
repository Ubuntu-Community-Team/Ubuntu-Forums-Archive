---
title: "amule help"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-11-17
I downloaded amule last week and have been trying to get it working. As for as I know, I have set up port forwarding correctly on my (wireless) router, but KAD is still firewalled.

Does anyone know how I can de-firewall KAD?

Cheers :)

---

### Post by spamzilla on 2006-11-17
Something weird is that sometimes files will download at say 2kb's, then slowly, the download speed will drop and stop downloading any files :/

---

### Post by spamzilla on 2006-11-17
Here's my iptables. I really don't see why amule won't download anything. Port forwarding in my router also contains the same open ports.

```
root@matt-laptop:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4662
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4672
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4665
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Anyone any ideas on my amule is being so stubborn?

---

### Post by TheWizzard on 2006-11-17
you'll need to be downloading a file for about 10 minutes before kad shows as 'green'.

---

