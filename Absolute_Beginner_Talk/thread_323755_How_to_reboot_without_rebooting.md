---
title: "How to reboot without rebooting"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by nickburns on 2006-12-22
I love that I have not had to reboot for 60 days now.  I have heard that if some of the packages require a restart you can bring linux through a process that is as close to restarting as possible, but keeping your uptime running.  So, is it possible?  what are the steps?

---

### Post by dbbolton on 2006-12-22
*sometimes *you can trick certain programs to think you've restarted by logging out and then back in

---

### Post by maxamillion on 2006-12-22
You can stop and restart services, but the installer will generally do that for you when it is needed. Normally what the reboot message is about is a kernel update and that requires a reboot.

---

### Post by bodhi.zazen on 2006-12-22
for a single server (for example GDM):
```
sudo /etc/init.d/<package_name> restart
```

For the whole tamale:
```
sudo init 2
```

---

