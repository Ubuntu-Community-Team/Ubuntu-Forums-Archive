---
title: "upgrading to 7.10 killed my wireless connection"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by razorbak on 2008-01-04
Having just downloading and installing the upgrade to 7.10 from 7.04 (fully updated) via my wireless network to internet.  The bloody thing won't run my wireless network card!
How do I get it working again when I cn't download the restricted drivers?  Should it not have downloaded them while the system was still working? Upgrade??

Not happy

---

### Post by razorbak on 2008-01-04
Needs:

Firmware for Broadcom 43xx chipset family

---

### Post by razorbak on 2008-01-04
Do I have to hard wire into a network to fix this problem?

---

### Post by gn2 on 2008-01-04
You could boot a 7.04 Live CD, use the wireless to download the firmware you need to your hard drive then re-boot into 7.10?

Or if you have an ethernet socket just use that.

---

### Post by insertAlias on 2008-01-04
> **razorbak said:**
> Do I have to hard wire into a network to fix this problem?

Yes, plug in, and go to :
System -> Administration -> Restricted Drivers Manager
You should see "Firmware for Broadcom 43xx chipset family" there.  Enable it, and then it will ask you to download another file (the actual firmware file).  Once that is done, your wireless should work again.

---

### Post by razorbak on 2008-01-05
Working fine now after plugging into hub.

---

