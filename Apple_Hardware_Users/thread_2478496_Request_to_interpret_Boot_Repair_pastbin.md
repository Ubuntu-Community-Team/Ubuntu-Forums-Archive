---
title: "Request to interpret Boot Repair pastbin"
date: 2022-08-28
forum: Apple Hardware Users
---

### Post by pdwilkins on 2022-08-28
Hi:  I am trying to install 18.10 on an old Apple MacBook Pro.  I made the mistake of upgrading a previous 18.10 installation to 20.10 and 22.04.  The last upgrade confronted me with unsupported nVidia driver issues.  I decided to go back to 18.10 but somehow lost my uefi boot capability.  I installed OSX Leopard, the version that came with the machine (I said it was old) and that works, but I can't simply install ubuntu from the live-dvd because I can get it to boot into uefi.

Here is my Boot Repair pastebin URL: [https://paste.ubuntu.com/p/FDzrY7syhH/](https://paste.ubuntu.com/p/FDzrY7syhH/)

Any help would be appreciated.

Thank you,
Peter

---

### Post by howefield on 2022-08-28
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by pdwilkins on 2022-08-28
Thank you, howefield!

---

### Post by oldfred on 2022-08-28
You should not install 18.10. That is EoL or end of life.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
If 20.04 worked better to use it, as it is LTS - long term support.

You have to shrink your Apple partition to make unallocated space for Ubuntu and boot Ubuntu live installer in UEFI boot mode.
If older system, a lightweight flavor may be better, but they only have 3 year support.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

[https://ubuntuforums.org/showthread.php?t=2377181](https://ubuntuforums.org/showthread.php?t=2377181)

---

