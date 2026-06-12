---
title: "About WPA Supplicant"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by eightysix on 2007-02-15
I have a quick question about WPA Supplicant. I currently have a wifi card that DOES NOT support WPA (Lucent Orinoco Gold). If I install WPA Supplicant, will I be able to log into my router via WPA with it?

---

### Post by wieman01 on 2007-02-15
If the card does not support it, wpa-supplicant won't be of any help to you. If the Windows driver for your card supports it (which is likely), then try "ndiswrapper" and use the Windows driver instead of the Linux one.

---

