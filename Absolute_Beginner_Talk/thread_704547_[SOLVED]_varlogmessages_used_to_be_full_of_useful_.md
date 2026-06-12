---
title: "[SOLVED] /var/log/messages used to be full of useful stuff, now it very bare, anythin"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by philinux on 2008-02-22
Has something changed with the logging system?

---

### Post by fatality_uk on 2008-02-22
> **philinux said:**
> Has something changed with the logging system?

Sorry not here. Mines chocka as usual :)

---

### Post by philinux on 2008-02-22
This all thats in there for today. Other days just the same. No boot messages.

```
Feb 22 11:05:28 philcb-desktop syslogd 1.4.1#21ubuntu3: restart.
Feb 22 11:05:33 philcb-desktop dhcdbd: Started up.
Feb 22 11:05:35 philcb-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Feb 22 11:05:39 philcb-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Feb 22 11:05:39 philcb-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Feb 22 11:05:39 philcb-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Feb 22 11:12:34 philcb-desktop syslogd 1.4.1#21ubuntu3: restart.
Feb 22 11:25:29 philcb-desktop -- MARK --
Feb 22 11:45:30 philcb-desktop -- MARK --
Feb 22 12:05:31 philcb-desktop -- MARK --
Feb 22 12:25:38 philcb-desktop -- MARK --
Feb 22 12:45:38 philcb-desktop -- MARK --
Feb 22 13:05:39 philcb-desktop -- MARK --
Feb 22 13:25:39 philcb-desktop -- MARK --
Feb 22 13:45:40 philcb-desktop -- MARK --
Feb 22 14:05:40 philcb-desktop -- MARK --
Feb 22 14:25:40 philcb-desktop -- MARK --
Feb 22 14:45:42 philcb-desktop -- MARK --
Feb 22 15:05:43 philcb-desktop -- MARK --
Feb 22 15:25:45 philcb-desktop -- MARK --
Feb 22 15:45:45 philcb-desktop -- MARK --
Feb 22 16:05:45 philcb-desktop -- MARK --
Feb 22 16:25:45 philcb-desktop -- MARK --
Feb 22 16:45:45 philcb-desktop -- MARK --
Feb 22 17:05:46 philcb-desktop -- MARK --
Feb 22 17:25:47 philcb-desktop -- MARK --
Feb 22 17:45:47 philcb-desktop -- MARK --
Feb 22 18:05:47 philcb-desktop -- MARK --
Feb 22 18:25:47 philcb-desktop -- MARK 
```

---

### Post by philinux on 2008-02-23
bump

---

### Post by philinux on 2008-02-23
Big OOOPPPSS.

I'd turned off klogd in services thinking that sysklogd would do the stuff. Wrong. :lolflag:

---

### Post by blacksm1th on 2008-02-25
> **philinux said:**
> 
I'd turned off klogd ....
Me too :lolflag: I spend all day to find why Firestarter didn't display network events. I was lucky to find this thread. Thank you :)

---

