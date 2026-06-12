---
title: "rogue network interfaces"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2007-03-25
I have rogue network interfaces showing up when I run ifconfig.

I am using wireless (ath0) to connect to network and sometimes use ethernet (eth0), however I have an entry for wifi0 which is doing nothing and needs to be removed.

I believe it is causing trouble with knetworkmanager because it thinks that is how I am connecting and hence it displays disconnected (despite the fact that I AM connected).

So my question, quite simply is how do I remove (delete) this interface (wifi0) completely?

---

### Post by schwascore on 2007-03-25
```
sudo vim /etc/network/interfaces
```

Hash out (#) the interface in question and that should remove it from view of the system.

---

