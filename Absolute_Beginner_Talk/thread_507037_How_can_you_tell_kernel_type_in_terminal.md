---
title: "How can you tell kernel type in terminal?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by dexwiz on 2007-07-22
Yep, what is the command for it?

---

### Post by mikewhatever on 2007-07-22
uname -r

---

### Post by FleetAdmiral74 on 2007-07-22
Not really sure...but when you boot up, it should say what version, something like Ubuntu, Linux Kernel v2. whatever...it should be there right next to the recovery mode and other OS's if you have any.

---

### Post by meatpan on 2007-07-22
As mentioned above, uname is a useful tool for viewing summary information about your os/architecture.  As a matter of habit, I am constantly running 'uname -a', which writes a single line summary of your system.  

If you want even more details about your kernel and the associated kernel configuration, consider using the 'sysctl' command.  Take a look at some of the information reported by this command by running 'sysctl -a | less'

---

