---
title: "urgent - lan/ethernet card"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-09-09
I'm using Feisty, and my onboard LAN card is busted. I need to get a new LAN card but can't seem to find one with drivers suitable for this kernel version. Can someone tell me which LAN card I can buy easily in New Delhi, India? I'd really prefer one that isn't too much trouble to install.
Thanks.

---

### Post by mendingo84 on 2007-09-09
you can buy any LAN card you want...it will work

---

### Post by kleo skywalker on 2007-09-09
> **mendingo84 said:**
> you can buy any LAN card you want...it will work

Er... the reason I posted was that I could not find a suitable LAN card. I tried one but it had drivers for much older versions of the linux kernel, and they had to compiled before they could be used.
So I'm looking for a brand name or technical specifications that I can take to a store (in New Delhi, India) and get a LAN card that works with this kernel version, and preferably has a driver that doesn't need to be compiled.

---

### Post by rich.bradshaw on 2007-09-09
You shouldn't need to install drivers unless it's a particularly "weird" card - did you try the LAN card you have?

If not, it's probably going to be auto detected by Ubuntu anyway - most drivers are built in.

If not, then there is a database of hardware that works with Ubuntu somewhere - maybe someone else has the link!

---

### Post by mendingo84 on 2007-09-09
from my experience, i have never had trouble with any of my LAN cards...maybe the LAN card you tried is an older one. but sincerely it should also work. anyway, maybe this [thread]("http://ubuntuforums.org/showthread.php?t=236810") will be relevant. you might have to edit you /etc/network/interfaces file in order to bring the interface up...

---

### Post by schorsch on 2007-09-09
Take a look in this [list]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards")  ... but many oher cards will work in addition to that as they use the same chipset.

---

