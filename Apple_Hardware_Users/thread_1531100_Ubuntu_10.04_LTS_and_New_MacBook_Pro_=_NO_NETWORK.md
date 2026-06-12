---
title: "Ubuntu 10.04 LTS and New MacBook Pro = NO NETWORK"
date: 2010-07-14
forum: Apple Hardware Users
---

### Post by Nasiom on 2010-07-14
Hi there,

Well, I got myself a new MacBook Pro 5,4 (Core2Duo 2.53 Ghz) and installed Ubuntu 10.04 on it. Installation went well except when I rebooted and realized I had no networking going at all.

Wireless is Broadcom BCM4322 and Ethernet is NVidia MCP79.

Tried to add the CD as resource in Synaptic Package Manager and install bcmwl-kernel-source and b43-fwcutter but getting error 1 or 4 or 6 during installation.  I have wiped and re-installed several times and the error number is never the same.

Anyways, I cannot use it at all for network access.

Anyone has a magic wand and know how to solve this issue?

Thanks

N

---

### Post by Nasiom on 2010-07-15
Ok Ethernet (wired) network is working when booted from the LiveCD.  My question is now, how do I find which drivers are in use when I'm booted from that CD?

Anyone can instruct how to find this so I could try to install them when I'm booted from the installed hard disk?

Thanks

N

---

### Post by alexmurray on 2010-07-15
Ethernet should use the forcedeth driver AFAIK and it really should work out of the box (especially since it worked via the livecd). bcmwl-kernel-source is the one you'll need for wifi, NOT b43 so make sure you only install bcmwl and that should also work. Sometimes I've found I have to install the driver a couple times till it actually works.

---

