---
title: "G3 Lombard modem problem"
date: 2006-10-30
forum: Apple PPC Users
---

### Post by linuxuser28 on 2006-10-30
I know Linux has a problem with win-modems but this is a Mac, and it still can't recognize the modem. However when I use to have Breezy Badger on it, the modem worked so I figure there must be a way to do this. Any ideas?

---

### Post by linuxuser28 on 2006-10-31
Have  run updates but still no luck.

---

### Post by Ptero-4 on 2006-11-17
Hi linuxuser28. add pmac_zilog to your Dapper's /etc/modules, reboot and if your modem works post about it here.

---

### Post by linuxuser28 on 2006-12-23
> **Ptero-4 said:**
> Hi linuxuser28. add pmac_zilog to your Dapper's /etc/modules, reboot and if your modem works post about it here.
That fixed it. Thanks. :D

---

