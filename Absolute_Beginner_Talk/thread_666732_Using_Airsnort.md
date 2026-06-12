---
title: "Using Airsnort"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by wolvish on 2008-01-13
I recently installed airsnort, due mainly to the fact that I'm at sea, and no-one in the crew remembers the router password on my deck. My understanding was that to gather the information needed, I have to input this:

```
 sudo airmon-ng start wifi0
```

However, when I do that, this comes up:

[I]Interface       Chipset         Driver

wifi0           Atheros         madwifi-ng/usr/sbin/airmon-ng: 91: wlanconfig: not found
iwconfig: unknown command "10"
up: error fetching interface information: Device not found

ath0            Atheros         madwifi-ng VAP (parent: wifi0)
[/I]

I don't know what to make of this, or have any clue how to use the program. If someone could give a few pointers, it would be much appreciated. I am running Kubuntu 7.10 Gutsy. I also installed aircrack and aircrack-ng, but I haven't been able to make that appear whatsoever.

---

### Post by mattismyname on 2008-01-13
Judging from the "Device not found" part, I would first verify that the driver for your wlan card is loaded (via 'lsmod') and that it is truly named wifi0 (and not wifi1, etc)

---

