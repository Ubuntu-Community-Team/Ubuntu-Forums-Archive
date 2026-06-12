---
title: "PCI error on MacBookPro"
date: 2021-08-11
forum: Apple Hardware Users
---

### Post by franekw on 2021-08-11
I have an old MacBookPro 15'' from 2009 (says middle late). I installed Ubuntu 20.04 LTS about two weeks ago. Everything was working all right but since yesterday it can't boot wither from disk or the Live CD.

The laptop was supposed to be for others as well. Therefor I did the following:
* made GRUB hidden
* Turned on Auto login
* Removed timer on selecting system/previous kernel
* installed NVidia drivers - interestingly, after installing the drivers, logo of the Ubuntu was replaced by NVidia splash :/

Yesterday, after login out, longing in and restarting the computer, the system stopped working. It hangs with black screen after showing Ubuntu logo again. When I try to boot it from Live USB, it shows the error:

```
[    0.395456] pci 0000:02:00.0 error -61 assigning properties
[    0.395456] pci 0000:02:00.0 error -61 assigning properties
```

I am afraid PCI error may indicate some hardware failure. This is an old laptop, which I almost gave up on but thought I would make it great again. If the computer is no longer usable, then I'll accept it but hope it is not the case.

Thanks.

---

### Post by QIII on 2021-08-11
Moved to Apple Hardware Users.

---

