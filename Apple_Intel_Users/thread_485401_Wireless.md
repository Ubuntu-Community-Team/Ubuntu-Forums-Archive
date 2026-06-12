---
title: "Wireless"
date: 2007-06-26
forum: Apple Intel Users
---

### Post by pandave on 2007-06-26
Hi all new to the forum and I read of a fella trying to turn off wireless services on a mini mac. I find this annoying as I don't need the service eating up resources as I don't need wireless on my internal network.  I think that the kernal is loading the service but can not be sure. There must be a way to stop wireless services from running at boot or just disable them altogether. Any help would be welcome.
Thanks Dave ...

---

### Post by benanzo on 2007-06-27
You can prohibit the kernel from loading the wireless module by doing:

```
sudo gedit /etc/modprobe.d/blacklist
```
Then add this to the bottom:
```

# Prohibit wireless module from loading
blacklist ath_pci

```

(this is for the Atheros chipset - which I think the Mini uses.)

---

