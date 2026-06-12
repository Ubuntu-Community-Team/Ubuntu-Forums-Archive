---
title: "Wifi iwlwifi Centrino N-100 on Asus X53SV can't do master mode"
date: 2012-10-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ellorenz on 2012-10-24
Hi to all.
My name's Lorenzo i bought an Asus X53SV with intel centrino wifi N-100, i installed ubuntu 12.10 and i'd need help to set up my wifi lan in master mode to do an hotspot to connect my android's tablet and phone. 
I tried every tutorial about it.
I installed hostapd, dhcpd and madwifi and wpasupplicant.
I tried with iwconfig but i can't set the master mode to apn. 
But all my attempts are faileds
```

using command sudo modeprobe --showconfig | grep wifi give me message
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# madwifi from loading by default. Use Jockey to select one driver

```The only success is the application wifi radar on android can see my hotspot connection but android can't connect.
With windows 7 and virtual router i can do it.
Somebody can help me ?

Thank's in advance

---

