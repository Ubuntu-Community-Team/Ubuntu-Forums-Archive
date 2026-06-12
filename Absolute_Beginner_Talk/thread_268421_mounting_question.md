---
title: "mounting question"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-09-30
is there a way so that when i reboot my partitions stay mounted?

---

### Post by cotcot on 2006-09-30
You can do that by editing /etc/fstab in terminal.
I guess you want to mount windows partitions. Here is a way to do :

[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

---

### Post by mendingo84 on 2006-09-30
thanks! i have another problem now...gksudo doesn't seem to be installed, do you know what i could use instead? becaue i tried synaptic but it seems broken!

---

### Post by aysiu on 2006-09-30
If you're using Ubuntu, paste this command in the terminal: ```
sudo aptitude update && sudo aptitude install ubuntu-desktop
``` If you're using Xubuntu, paste this command in the terminal: ```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

---

