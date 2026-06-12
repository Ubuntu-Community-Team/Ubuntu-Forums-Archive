---
title: "Wrong permissions on /etc/sudoers"
date: 2008-07-13
forum: Beginner Team
---

### Post by jax804 on 2008-07-13
Somehow I messed up the permissions on the file /etc/sudoers

When I enter the command sudo visudo, I get the followinmessage:
sudo: /etc/sudoers is mode 0770, should be 0440

How do I get the permission changed to 0440????

---

### Post by sisco311 on 2008-07-13
Reboot the computer in Recovery Mode and execute this commands
from the root shell:
```
chmod 0440 /etc/sudoers
exit
```
Boot in normal mode.

---

