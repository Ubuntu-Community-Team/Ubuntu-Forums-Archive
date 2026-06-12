---
title: "[SOLVED] can't login after deactivating service"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by fred the wise on 2007-07-22
ok here is my problem:

I deactivated a service (think was cpufreq) from boot of the system, and suddnly it crashes and now I can't login..

[COLOR="red"]_Is there a particular mode to activate/deactivate services from the command line (recovery mode)???_[/COLOR]

Thank for your help..
fRed

---

### Post by tomcheng76 on 2007-07-22
update-rc.d servicesname defaults  should able to add them back to the boot process

---

### Post by fred the wise on 2007-07-22
well it seems all services are linked to system startup..so maybe the problem's not there

---

### Post by fred the wise on 2007-07-22
are there any ways to check startup configuration files needed to login properly? 
I can't use windows for more than few minutes.. :)

---

### Post by fred the wise on 2007-07-25
all right, I just had to enter in the graphical mode

---

