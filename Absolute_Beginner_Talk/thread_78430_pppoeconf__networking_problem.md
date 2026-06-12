---
title: "pppoeconf / networking problem"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by dross on 2005-10-18
Hello,

I just changed ISP's and am having a problem getting online.  My dsl worked flawlessly with no configuration on my old set-up, but on my new cable modem none of the common suggestions are working.  In Admin/Networking/Connections, the Ethernet connect is active and the configuration is set to DHCP ("This device is configured" is checked).  I've tried deactivating the ethernet connection and reactivating, but that does nothing.  pppoeconf gives me the following message:  

"Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables.  Another reason for the scan failure may also be another running pppoe process which controls the modem."  

Searching through the forum, I've seen a lot of folks getting this message, but I have not found any fix yet.  Help/suggestions would be much appreciate. Thanks!

---

### Post by adwait on 2005-10-18
Maybe your new provider doesn't run on PPPoE?

---

### Post by dross on 2005-10-18
OK, how would I find that out, and if my provider does not support pppoe, any suggestions on how to proceed??

---

### Post by adwait on 2005-10-18
Depends on what your ISP uses. Maybe he uses PPPoA. Or maybe some other protocol. Its possible that they have given you a ROUTER instead of a MODEM, which authenticates on its own. In that case, just use the IP of your router as your DNS server. Ask your ISP for specs of their service, exactly what they use to connect, and what to they suggest to connect in Linux.

---

