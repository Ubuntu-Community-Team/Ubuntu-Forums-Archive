---
title: "Yet another wifi problem"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Shmook on 2007-04-11
So everything's been going just fine after installing ndiswrapper for my Linksys piece of crap wireless adapter, until yesterday.

The situation now is that "ndiswrapper -l" comes back with the correct driver and the hardware recognized, just like it always had been.

iwconfig comes back looking right as rain, as does lsusb

(I'm typing this on another comp which is why I'm not copying the results from those commands)

The only difference is that Network Manager doesn't give me the wireless option at all.

The only thing I can imagine as a cause was that I updated a few linux-headers...now I'm not sure exactly what they were, so if it's required I'll need someone to tell me the command to find exactly what was installed -- unless anyone's got any other ideas.

Thanks a bunch!

---

### Post by Nxion on 2007-04-11
This sounds like a misconfiguration issue to me

post what the output is of this command is if you can


```
tail /etc/network/interfaces
```Thanks

---

### Post by Shmook on 2007-04-11
tail /etc/network/interfaces gives:

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid (network name)
wireless-key s: (key)

---

### Post by Nxion on 2007-04-11
Did you download the resolv.conf file as well when you installed NetworkManager ?

---

### Post by Shmook on 2007-04-11
...I'm not sure, but the thing is Network Manager has worked fine until lately.

---

