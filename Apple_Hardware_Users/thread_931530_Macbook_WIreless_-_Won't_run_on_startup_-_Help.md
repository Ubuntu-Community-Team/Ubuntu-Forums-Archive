---
title: "Macbook WIreless - Won't run on startup - Help"
date: 2008-09-27
forum: Apple Hardware Users
---

### Post by purxaoc on 2008-09-27
I have installed the ath9k(generic) drivers, and the wireless has worked in the past.  Once I did an update and restarted my Macbook (2.1 - Core 2 Duo) into Ubuntu again, the wireless has not been working since.

I added "ath9k" to the list in the modules file, however upon start up the only available option is wired networking, which I am currently plugged into.

Did I edit this file wrong?  Has the driver been corrupted or removed somehow, or possible is has an extension other then ath9k?  I don't know how to run the driver via terminal manually to check.  Ideas?

Thanks so much..

---

### Post by cyberdork33 on 2008-09-28
use 'lsmod' and check that the ath9k module is loaded. If not, you can load it via 'sudo modprobe ath9k'.

If you updated the kernel and had used volanin's script to get ath9k, you probably just need to reinstall it again.

---

