---
title: "GRUB error 21"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by niobie on 2006-02-25
I have an external USB HD and i have tried to install ubuntu on it. But when i restart my computer it doesn't iniciate the boot menu. It gives me a GRUB error 21. Even when i unplug my USB HD. Does anyone have a solution?

oh n sorry about my bad english :neutral:

---

### Post by az on 2006-02-25
Error 21 means that grub cannot find the partition where the rest of it is.  It uses the information from BIOS to locate it.   Your bios does not know about your usb drive.

---

