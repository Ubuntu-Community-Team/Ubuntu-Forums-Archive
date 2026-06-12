---
title: "MacBookPro4,1 wireless does not work under Jaunty"
date: 2009-08-30
forum: Apple Hardware Users
---

### Post by MonkeyPlus on 2009-08-30
I've installed Jaunty on a MacBookPro4,1, the proprietary Broadcom drivers did not work, so I disabled them and attempted to work around with ndiswrapper. No luck at all.

Entry for lspci:

```
0b:00.0 Broadcom Corporation BCM4328 802.11a/b/g/n (rev 05)
```

lshw -C network gives:

```

description: Network Controller
product: BCM4328 802.11a/b/g/n
vendor: Braodcom Corporation
physical id: 0
bus info: pci@0000:0b:00.0
version: 05
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=b43-pci-bridge latency=0 module=ssb

```

As I mentioned, I have already tried the solutions suggested elsewhere for forcing ndiswrapper to be used over ssb, however they do nothing at all.

All the solutions I have found in the Apple section have been for older versions. Is Apple support being abandoned?

---

### Post by MonkeyPlus on 2009-08-30
Found the solution after more searching. I entered:

sudo rmmod ssb wl
sudo modprobe wl

This works with current kernel (.15) but doesn't persist past reboot. Still trying to fix it.

---

### Post by beny-4.56 on 2009-08-31
> **MonkeyPlus said:**
> Found the solution after more searching. I entered:

sudo rmmod ssb wl
sudo modprobe wl

This works with current kernel (.15) but doesn't persist past reboot. Still trying to fix it.

i think we don't need the module `ssb` at all. so just add it to /etc/modprobe.d/blacklist.conf

```

$ echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf

```

---

### Post by MonkeyPlus on 2009-08-31
The first command is now not needed. The second command I still have to do every time I start up. Still trying to find where to put it.

---

### Post by amd-64 on 2009-08-31
Modules that get loaded on start-up are in /etc/modules
Add it as follows
```

echo "wl" | sudo tee -a /etc/modules

```

---

### Post by MonkeyPlus on 2009-09-01
Thanks, I have done that and will report back next reboot

---

### Post by MonkeyPlus on 2009-09-02
That nailed it, thanks

---

