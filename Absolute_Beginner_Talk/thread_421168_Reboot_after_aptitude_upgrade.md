---
title: "Reboot after aptitude upgrade?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by virx on 2007-04-24
If I use cronjob for updating Feisty system:
```
aptitude -y update && aptitude -y upgrade && aptitude -y dist-upgrade
```

Is reboot neccassary after that or changes take effect without restarting?

---

### Post by Seisen on 2007-04-24
If its a major change then a reboot is required, like updating the kernel. If its nothing big than you don't have to worry about rebooting the computer.

---

### Post by Pobega on 2007-04-24
The only thing you'll actually need to reboot for is a kernel upgrade; Everything else should automatically happen (Of course, you'll need to restart the updated program if it's running).

---

### Post by virx on 2007-04-25
Thx

For servers you don't do dist-upgrade?
Should I add cronjob for reboot once week?

---

### Post by az on 2007-04-25
> **virx said:**
> Thx

For servers you don't do dist-upgrade?
Should I add cronjob for reboot once week?

I would not reboot automatically, I would do it by hand.

You may also need to reboot after HAL gets updated.

Yes.  Servers  need to keep up-to-date with updates.

---

### Post by xyz on 2007-04-25
When you need to reboot, there should be an icon that asks you to do so on the top panel.

---

### Post by az on 2007-04-25
> **xyz said:**
> When you need to reboot, there should be an icon that asks you to do so on the top panel.

Not if you are running a headless server.  I wonder if a message is sent to the user in this case.  On my feisty server box, /var/log/news/* is empty, but I have never checked after I dist-upgraded a new kernel/hal.

---

### Post by virx on 2007-04-26
Ok, I will schedule reboot for weekends.
(Too bad, Ubuntu won't reboot automatically after update like Windows does.)

---

