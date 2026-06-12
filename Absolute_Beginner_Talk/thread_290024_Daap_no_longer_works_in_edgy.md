---
title: "Daap no longer works in edgy"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by mrvgarg on 2006-10-31
Daap was working fine in breezy. Then I did a clean install of edgy and daap is no longer working. I have not changed any settings on the itunes server. Plz help

---

### Post by makuk66 on 2006-11-08
Fixed here by doing:

- Confirm System->Administration->Services has mDNS service discovery.
- Change /etc/default/avahi-daemon AVAHI_DAEMON_START=0 to AVAHI_DAEMON_START=1
- sudo /etc/init.d/avahi-daemon start

---

