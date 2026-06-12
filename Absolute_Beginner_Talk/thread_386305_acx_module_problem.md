---
title: "acx module problem"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Angry penguin on 2007-03-16
For some reason my wireless module is not loading on startup, everytime i login i have to do:

modprobe acx
sudo /etc/init.d/networking restart

to get it working.

I have put acx into the /etc/modprobe.conf file. Any ideas?

---

### Post by terdon on 2007-03-17
Try adding acx to /etc/modules instead of /etc/modules.conf

---

### Post by Angry penguin on 2007-03-17
Sorry, it is in /etc/modules not /etc/modprobe.conf

---

