---
title: "Macbook Pro 2,1, wi-fi (ath9k) issues on resume from suspend"
date: 2008-12-06
forum: Apple Hardware Users
---

### Post by acewin on 2008-12-06
On my Macbook Pro 2,1 with 8.10 and latest ath9k(from compat-wireless) driver, I am unable to connect to a WPA2 secured network after resuming from suspend. However, removing the ath9k module and enabling it again seems to work fine.

Also, in my /etc/default/acpi-support, I have specified ath9k to be removed before suspending and to be enabled on resume, still does not work unless I manually reload the module.

TIA, for any help on this.

---

