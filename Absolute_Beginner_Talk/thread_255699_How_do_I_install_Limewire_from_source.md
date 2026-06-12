---
title: "How do I install Limewire from source?"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-09-11
I just downloaded Limewire source off the limewire website, there was a another linux download for RPM but I don't think Ubuntu is RPM, anywho, can someone please tell me how to install it from source.

---

### Post by Qrk on 2006-09-11
Try frostwire... it comes in .deb format.

But if you insist on using limewire, install the package "build-essential" then cd to the limewire source directory (un tar it first) and run these commands in this order.

```
./configure
make
sudo make install
```

---

### Post by abu-fatu on 2006-09-11
i installed limewire rpm using alien download LimeWireLinux>rpm to desktop.
in terminal type: "cd Desktop" after type: "sudo alien -i LimeWireLinux.rpm"
aline does the rest then go to apps-internet-Limewire. it's that easy. i believe that you must have java installed from aoutomatix.

---

