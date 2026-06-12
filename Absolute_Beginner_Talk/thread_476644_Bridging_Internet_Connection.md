---
title: "Bridging Internet Connection??????"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by kiranlin on 2007-06-17
Dear friends i am new to linux field i have instaled ubuntu latest version but it working fine but
i have boardband internet but it is bridging connection[where username & password] are given who to make a new connection in ubuntu linux........................


thanks in advance

---

### Post by zvacet on 2007-06-17
system>administration>network>select your modem>properties>select type of connection(dhcp,static)>close>DNS tab>delete address you find there and add your nameservers<close

```
pppoeconf
```

---

