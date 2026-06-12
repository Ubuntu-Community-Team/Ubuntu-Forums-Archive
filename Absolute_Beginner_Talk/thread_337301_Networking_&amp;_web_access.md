---
title: "Networking &amp; web access"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by darkcyber on 2007-01-12
Ok, I've run ubuntu on livecd and installed it to 2 different pc's.  To say the least, I'm having loads of problems with it.  Here's one.  I can't find any errors in my network devices and I have enter my static private ip's, subnet and domain servers and I can't access the internet and can't even ping my router.  I've even tried DHCP and no luck.

Both of my pc's are running different MSI motherboards with Realtek gigabit NIC.  

Should your network stuff work from just installing ubuntu or do you usually have to install other things or do something else?

---

### Post by jas0 on 2007-01-12
First try running:

```
ifconfig
```

If you don't see anything (except for a "lo" infterface) try the following:

```
ifconfig eth0 up
dhcpcd eth0 (not sure about this one on Ubuntu. I'm sure someone will correct me if I'm wrong)
```

---

### Post by darkcyber on 2007-01-12
Thanks I will give that a try.  I'm doing a fresh new installation again right now.  I'll see how it goes.

---

