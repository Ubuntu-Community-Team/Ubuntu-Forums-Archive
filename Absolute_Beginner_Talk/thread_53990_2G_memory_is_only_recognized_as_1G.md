---
title: "2G memory is only recognized as 1G"
date: 2005-08-03
forum: Absolute Beginner Talk
---

### Post by ilmw on 2005-08-03
Hi,

I searched the forum but couldn't find answer. I have 2G memory (2X1G) on dell 700m running ubuntu. But ubuntu only recognizes 1G, while Mandrake can detect 2G and made good use of it. Is there a workaround for this? Thanks a lot!

ilmw

---

### Post by bored2k on 2005-08-03
[QUOTE=ilmw]Hi,

I searched the forum but couldn't find answer. I have 2G memory (2X1G) on dell 700m running ubuntu. But ubuntu only recognizes 1G, while Mandrake can detect 2G and made good use of it. Is there a workaround for this? Thanks a lot!

ilmw[/QUOTE]
 Open up Synaptic (Upper panel - System - Administration - Synaptic PKG Manager), click on Reload then search for and install linux-686. After that is done, reboot and select Ubuntu 686 from the boot menu. 

Why ? The 386 kernel supports up to 900 megs of ram.-

---

### Post by ilmw on 2005-08-03
Thanks a lot! Will give a try now ..

[QUOTE=bored2k]Open up Synaptic (Upper panel - System - Administration - Synaptic PKG Manager), click on Reload then search for and install linux-686. After that is done, reboot and select Ubuntu 686 from the boot menu. 

Why ? The 386 kernel supports up to 900 megs of ram.-[/QUOTE]

---

### Post by ilmw on 2005-08-03
YES, I can see 2GB memory now. Thanks a lot, bored2K!

---

### Post by bored2k on 2005-08-03
[QUOTE=ilmw]YES, I can see 2GB memory now. Thanks a lot, bored2K![/QUOTE]
 Rock _on.

---

