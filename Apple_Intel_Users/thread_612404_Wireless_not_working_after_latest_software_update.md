---
title: "Wireless not working after latest software update"
date: 2007-11-13
forum: Apple Intel Users
---

### Post by schauerlich on 2007-11-13
Synaptics installed a bunch of updates this afternoon (there were 40 or so, I didn't take the time to look through and see what each one was). I ducked into OSX for a moment, and when I booted back into Ubuntu, my wireless wasn't working. I get an option for Wired Connection (greyed out) and an option for Manual Configuration, but nothing for wireless. Wireless works fine in OSX and the other computer on the same connection. What should I do?

---

### Post by cyberdork33 on 2007-11-13
> **EDavidBurg said:**
> Synaptics installed a bunch of updates this afternoon (there were 40 or so, I didn't take the time to look through and see what each one was). I ducked into OSX for a moment, and when I booted back into Ubuntu, my wireless wasn't working. I get an option for Wired Connection (greyed out) and an option for Manual Configuration, but nothing for wireless. Wireless works fine in OSX and the other computer on the same connection. What should I do?

If the kernel was updated, this is normal. you need to recompile madwifi.

EDIT: Just checked, the Kernel modules packages were updated... which essentially means that the madwifi package was overridden.

---

### Post by schauerlich on 2007-11-13
Thanks, it's working fine now.

---

### Post by Levo75 on 2007-11-14
Does anyone know if the Broadcom BCM4328 works in gutsy now?

---

### Post by cyberdork33 on 2007-11-14
> **Levo75 said:**
> Does anyone know if the Broadcom BCM4328 works in gutsy now?

It has always worked with ndiswrapper... except the new Macbooks for some reason.

---

