---
title: "Root sudo gksudo"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by mimsmall on 2007-03-19
Very frustrated. Constantly being told I don't have permission. It is so agravating because I'm the only person using my laptop. How can I be root as in other linuxOSs and then log back in as a user? I hate being told I don't have permission. The older I get the more ticked off I become.:(

---

### Post by Najand on 2007-03-19
Well, working as root is exteremly dangerous, that is why in UBUNTU as a default there is no root password has been defined. There are a few ways to use Root though. Err... Like using "sudo -s" command and using your own password or just simply define a password for root.  Anyway instead of using gksudo it is better to use gksu... It saves a lot of time.

---

### Post by Moeru on 2007-03-19
Using sudo or gksudo is far more secure and builds better habits. I believe, for a terminal session, its sudo -s and it'll keep the root login running as long as that terminal session is open.

---

### Post by aysiu on 2007-03-19
This will help you:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

