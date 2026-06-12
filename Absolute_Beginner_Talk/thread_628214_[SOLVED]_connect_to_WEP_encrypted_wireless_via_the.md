---
title: "[SOLVED] connect to WEP encrypted wireless via the terminal"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-12-01
Hey,

what is the command for connecting to a WEP encrypted wireless network?
I know the ESSID and the WEP hex code. Its DHCP :)

thanx,
sv

:popcorn:

---

### Post by kelbizzle on 2007-12-01
```

iwconfig eth1 ap (what ever your ap mac address is)
iwconfig eth1 essid (name of your wireless network)
iwconfig eth1 key s:passphrase
dhclient eth1

```

---

### Post by staticvoid on 2007-12-01
yay :) thanks a bunch.


sv

---

