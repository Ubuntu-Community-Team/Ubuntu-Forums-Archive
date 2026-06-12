---
title: "'modprobe ath_pci' doesn't work with madwifi"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by arseniy on 2008-04-26
I made and installed madwifi, but when I try:
```
modprobe ath_pci
```

I get:
```
FATAL: Error inserting ath_pci (/lib/modules/2.6.22-14-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

What does that mean>

---

### Post by benanzo on 2008-04-26
You need to relink the module with the kernel.

```

$ sudo depmod -ae
$ sudo modprobe ath_pci

```

This is required especially if you compile a new module with the same name as an old one, in this case ath_pci.ko.

---

