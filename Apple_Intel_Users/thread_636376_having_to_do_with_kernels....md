---
title: "having to do with kernels..."
date: 2007-12-09
forum: Apple Intel Users
---

### Post by onlyproductions on 2007-12-09
i think...
anyway is there any distro of linux which has the correct (i hope to god im using the word correctly) kernels that would support a macbooks wi-fi?
and will hardy hedron support it?

---

### Post by cyberdork33 on 2007-12-09
no

Apple uses atheros and broadcom chipsets in their machines. These have closed, proprietary modules that cannot be included in the kernel.

I believe that Atheros has given some information finially, and is helping to create an open driver, but even then, it might require loading firmware to work, which would not be included in the kernel. Complain to the manufacturer.

This does not mean that your WiFi card will not work out-of-the-box in future Ubuntu distros, but at the moment it will not.

madwifi or ndiswrapper will work to get Wi-Fi working.

---

