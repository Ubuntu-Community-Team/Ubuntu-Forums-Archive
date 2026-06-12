---
title: "Ubuntu laptop hogging ALL bandwidth? Is there a fix?"
date: 2014-04-28
forum: Any Other OS
---

### Post by jrozo17 on 2014-04-28
Alright so I've been noticing something strange since I installed Elementary OS (Ubuntu 12.04) on my laptop. Whenever it's booted up and running, I literally can't use any other device in my house. Signing in on my PS3 just leaves me with an error or is extremely laggy, and using online apps or Safari on my Ipod touch is near impossible.

However, once I shut down my laptop, I notice that all devices return to normal and share bandwidth in harmony.

Is there a fix to this, or is it a glitch that can only be reported? I have no start-up programs, and rarely use anything heavy such as torrent clients... So essentially there shouldn't be a problem.

Thanks everyone.

---

### Post by kostkon on 2014-04-28
I'm assuming you have a broadcom card and use the wl driver; but to make sure, what's the output of
```
lspci | grep -i network
```
You could try disabling the closed source wl driver and rebooting and ubuntu should then use one of the 2-3 open source drivers that are available for broadcom cards in its place.

I don't know anything about ElementatyOS, but in Ubuntu you would disable the driver by opening your updater, clicking on Settings and then on Additional Software/Drivers.

---

### Post by jrozo17 on 2014-04-28
> **kostkon said:**
> I'm assuming you have a broadcom card and use the wl driver; but to make sure, what's the output of
```
lspci | grep -i network
```
You could try disabling the closed source wl driver and rebooting and ubuntu should then use one of the 2-3 open source drivers that are available for broadcom cards in its place.

I don't know anything about ElementatyOS, but in Ubuntu you would disable the driver by opening your updater, clicking on Settings and then on Additional Software/Drivers.

Here's what it gives me:

```
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
```

Elementary is essentially Ubuntu, so I'll try disabling it like you suggested. What I find weird though is, shouldn't the official closed source driver work more efficiently than an open source driver? That's the only reason why I enabled it.

---

### Post by jrozo17 on 2014-04-28
Alright so I disabled the proprietary driver and reverted to open source, and nothing's changed. :( I guess I'll have to turn off my laptop every time I use another device.

---

### Post by kostkon on 2014-04-29
> **jrozo17 said:**
> Alright so I disabled the proprietary driver and reverted to open source, and nothing's changed. :( I guess I'll have to turn off my laptop every time I use another device.
What's the output of
```
nm-tool
```

---

### Post by sandyd on 2014-04-29
**Moved to Other OS**

---

