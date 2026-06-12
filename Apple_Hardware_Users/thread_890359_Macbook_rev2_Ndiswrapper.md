---
title: "Macbook rev2 Ndiswrapper"
date: 2008-08-15
forum: Apple Hardware Users
---

### Post by kestaz on 2008-08-15
How to make ndiswrapper to work after suspend ? I don't how to unload ndiswrapper driver before suspend.

Actually i am using Debian and i want to find some instructions how to compile ath9k by own. Or it's too hard ? 

Thanks

---

### Post by cyberdork33 on 2008-08-15
> **kestaz said:**
> How to make ndiswrapper to work after suspend ? I don't how to unload ndiswrapper driver before suspend.
open  /etc/defaults/acpi-support and add 'ndiswrapper' in the MODULES line. This should automatically unload the module on suspend, and reload it when you wake.

> **kestaz said:**
> Actually i am using Debian and i want to find some instructions how to compile ath9k by own. Or it's too hard ?
There are links and information in this thread:
[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097)

---

