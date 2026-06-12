---
title: "MAC address"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-10-09
How can I find the MAC address of my file server?  I know the ip... :confused:

---

### Post by taurus on 2007-10-09
```
/sbin/ifconfig
```

---

### Post by mramsey on 2007-10-09
> **taurus said:**
> ```
/sbin/ifconfig
```

That gave me the HDware of my computer.  I need my file servers mac address. is there a way to query from terminal?

---

### Post by expatCM on 2007-10-09
The file server does not have a Mac address.   A Mac address is a unique identification which relates to an individual piece of hardware.  What you are probably being asked for is the Mac address of the primary Ethernet card.

[http://en.wikipedia.org/wiki/MAC_address](http://en.wikipedia.org/wiki/MAC_address)

---

### Post by Whiffle on 2007-10-09
'arp' might show it.

---

### Post by cwood06 on 2007-10-09
use arp -av give it a sec and itll tell ya the mac address. You will only see the mac address if you are on the same network as the file server

---

