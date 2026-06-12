---
title: "graphics card big problem"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-10-13
I have accidentally deleted my nvidia drivers and when I attempt to replace them with Envy I get this answer :
There was an error in the installation process. You can see the log file /var/log/envy-installer.log

Anyone help?

One more thing, when I try to run updates I get this:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by 67GTA on 2007-10-13
Run > sudo dpkg --configure -a in a terminal, and just install the driver with the restricted manager.

---

### Post by Benbow on 2007-10-13
What is the "restricted manager" ? I have followed the above and nothing happened.

---

### Post by 67GTA on 2007-10-13
The command I gave you just basically reset dpkg. It was interrupted. Open the menu, and go to SYSTEM>ADMINISTRATION>RESTRICTED MANAGER.

---

### Post by Benbow on 2007-10-13
Brilliant! Problem solved. Thank you very much.

---

