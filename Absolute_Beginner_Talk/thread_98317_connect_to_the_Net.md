---
title: "connect to the Net"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by salmanal on 2005-12-02
I ran the Live Cd version of Breezy Badger (5.10) and I can't seem to get it connected.

When it boots/configures, I see it setting up DHCP. When I try to
configure eth0, I set it up as DHCP. I even try entering the DNS information for my ISP
and still get no where.

Is there a place to configure DSL?

thanks

---

### Post by cwaldbieser on 2005-12-03
[QUOTE=salmanal]I ran the Live Cd version of Breezy Badger (5.10) and I can't seem to get it connected.

When it boots/configures, I see it setting up DHCP. When I try to
configure eth0, I set it up as DHCP. I even try entering the DNS information for my ISP
and still get no where.

Is there a place to configure DSL?

thanks[/QUOTE]
You can try to request an IP address from a DHCP server again with:
```

$ sudo dhclient eth0

```

---

