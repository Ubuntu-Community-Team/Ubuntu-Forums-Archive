---
title: "Please help: /etc/init.d/gdm stop failed"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by eewujian on 2008-01-15
I'm trying to install nVidia GeForce 8600 linux driver. For which I was prompt to exit X server. Ctrl+Alt+Backspace didn't work. I typed
sudo /etc/init.d/gdm stop
The system displayed the following message
* Starting anac(h)ronistic cron anacron   [ok]
* Starting deferred execution scheduler atd [ok]
* Starting periodic command scheduler crond [ok]
* Checking battery state ...  [ok]
* Running localboot scripts (/etc/rc.local) [ok]
Then the system halted.
I pressed Ctrl+Alt+Del. The system displayed
Stop gnome display manager. And bla-bla-bla then get rebooted.
My system: Dell Inspiron 531 with AMD 64 AthlonX2 processor.  Ubuntu 7.10 32-bit
I'm an absolute beginner. Please help! Thanks!

Jim

---

### Post by sumguy231 on 2008-01-15
After you stop GDM you'll need to hit Ctrl+Alt+F1 to get to a terminal.

---

