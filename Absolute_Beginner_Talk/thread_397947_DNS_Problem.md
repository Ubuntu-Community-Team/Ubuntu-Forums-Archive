---
title: "DNS Problem"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-03-31
I set /etc/hosts to "127.0.0.1 localhost.localdomain localhost
192.168.0.100 server1.example.com server1

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts"

I want the network to have the domain name server1.example.com, and when I type hostname -f, it says "Hostname unknown"

---

### Post by nixclusive on 2007-03-31
Then you'll need to keep it like this:

```
127.0.0.1 server1.example.com server1 localhost.localdomain localhost
```

---

