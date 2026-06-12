---
title: "rt61 chipset? Or rt2500?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by .oops on 2007-03-21
I have a CWP-854 PCI wireless card, and according to ndiswrapper's list, it says that it has a rt2500 chipset:

```
Card: CNet CWP-854 Wireless-G PCI Adapter 
**Chipset: RT2500 **
pciid: 1814:0201 (rev 01) 
Driver: Windows 2000 drivers from installation CD, driver version 11/27/2003, 2.01.00.0000 
Other: using NdisWrapper? version 1.0rc2, Debian unstable, Kernel 2.6.10 
Other: I just tested this device with ndiswrapper and works great
```

However, when I type ***iwconfig*** in the terminal, it says **ra0** followed by **rt61**. Could ndiswrapper list be wrong? :S

---

### Post by Bachstelze on 2007-03-21
```
lspci -n | grep $(lspci | grep Network | awk '{print $1}')
```

What do you get ?

---

### Post by chili555 on 2007-03-21
It seems to me if it shows up under iwconfig, it's working now. Why ndiswrapper?

Are you connecting?

---

### Post by .oops on 2007-03-21
It shows under iwconfig, but it doesn't show me ESSID, and yet I've configured it in Network Manager. But now I'm not using ndiswrapper, I just wanted to know what chipset I have install the native drivers.

[QUOTE=HymnToLife]What do you get ?[/QUOTE]

Sorry I'm not in Ubuntu right now. I don't have a ethernet connection, and besides that I need to re-install. However, I'll post it here later.

**Edit:** Where can I download the native drivers from Ralink (not serialmonkey) for rt61?

---

### Post by .oops on 2007-03-21
Can I get any help on this please?

---

### Post by Bachstelze on 2007-03-21
Aren't they on the Ralink website ?

---

### Post by .oops on 2007-03-21
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

Apparently not, unless I have some serious eye problems! x)

---

