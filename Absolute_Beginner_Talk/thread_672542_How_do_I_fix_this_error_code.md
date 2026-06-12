---
title: "How do I fix this error code?"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by alexstein0808 on 2008-01-19
I am trying to install new package files but keep on getting an error code saying :
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache-> open() failed, please report.

I'm new to Ubuntu and so don't really know what to do, please please please help me if you can.

---

### Post by SunnyRabbiera on 2008-01-19
this is a common error, its not much to worry about but you may need to open up a terminal and type in sudo apt-get update to resolve it.

how are you installing packages?

---

### Post by oldos2er on 2008-01-19
In a terminal, type "sudo dpkg --configure -a"

---

### Post by SunnyRabbiera on 2008-01-19
> **oldos2er said:**
> In a terminal, type "sudo dpkg --configure -a"

this also works if what i said doesnt work, like i said though this error is minor and quite common

---

