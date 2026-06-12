---
title: "How to start an script in terminal at startup as root"
date: 2013-05-17
forum: Any Other OS
---

### Post by rng on 2013-05-17
How can I start a script in terminal at startup as root? I am running Cinnamon desktop on linux-mint-13 (based on ubuntu precise). Thanks for your help.

---

### Post by Perfect Storm on 2013-05-17
Moved to Other OS/Distro Support.

---

### Post by Habitual on 2013-05-18
> **rng said:**
> How can I start a script in terminal at startup as root? I am running Cinnamon desktop on linux-mint-13 (based on ubuntu precise). Thanks for your help.

Never use your computer **as root**.
stick whatever in /etc/rc.local and it will run after all system daemons have started.
It's the fast and easy method and perfectly ok to do.

Cron is another way to run still 'as root'

make backups before edit.

---

### Post by Cheesehead on 2013-05-18
Use Upstart. That's exactly what it's for.
[http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

---

