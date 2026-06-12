---
title: "Wireless Issue continued..."
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Lazy-buntu on 2008-04-14
Alright here we go again, this time I have a wired connection.

I've got the driver installed with ndiswrapper:

sudo ndiswrapper -l:
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

iwlist scan eth1 shows the wireless networks around me

Anyway, if I connect to my network (who has a 128 bit WEP key (hex) and a broad casted ESSID) network-admin or whatever pops up and asks for the key, I give it the correct key, but no wireless.

I try to run sudo dhclient eth1 and I get offers, but it's like ubuntu won't accept them. I have also tried a static IP address, but that doesn't work either.

Is there a problem with 128 bit hex WEP keys in gutsy gibbon? Or, has anyone had a similar problem that has insight?

Thanks.

---

### Post by bobplano on 2008-04-14
I think the WEP key is fine. try blacklisting the bcm43xx drivers

in /etc/modprobe.d/blacklist

add```
blacklist bcm43xx
```

if it isn't already there

---

