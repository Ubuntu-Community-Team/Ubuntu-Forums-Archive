---
title: "Can No Longer Print"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Covalent Bond on 2008-01-09
After performing a suggested upgrade involving CUPSYS (unfortunately did not pay close attention to all that was to be upgraded) I received the following error message:   E: CUPSYS: subprocess post-installation script returned error exit Status 1. I looked at what appeared to be related posts, but did not find a solution I understood. I uninstalled CUPSYS and re-installed it only to get the same message.  I can not print nor can I configure a printer in synaptic.  Any help would be appreciated since I do need to print from Ubuntu.
Thanks
CB
__

---

### Post by mikeyphi on 2008-01-10
> **Covalent Bond said:**
> After performing a suggested upgrade involving CUPSYS (unfortunately did not pay close attention to all that was to be upgraded) I received the following error message:   E: CUPSYS: subprocess post-installation script returned error exit Status 1. I looked at what appeared to be related posts, but did not find a solution I understood. I uninstalled CUPSYS and re-installed it only to get the same message.  I can not print nor can I configure a printer in synaptic.  Any help would be appreciated since I do need to print from Ubuntu.
Thanks
CB
__

Try this - it won't hurt!
Open a terminal and enter:
sudo dpkg --configure -a

---

