---
title: "Root with ubuntu"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by MoshNet on 2005-10-18
When I installed ubuntu, it asked me to make a user name, which I login with. But when I try to use commands like apt-get and such, and tells me I do not have root privelages. How can I login as root ? Is there a default password ? This sucks. :???:

ssga@:~$ apt-get install aim
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ssga@:~$

---

### Post by Pablo_Escobar on 2005-10-18
Do not use root account, please - You can mess up Your system badly.
When You want to issue a root command, type "sudo" first - like "sudo apt-get ...".

---

### Post by MoshNet on 2005-10-18
Rock on.. you are awesome. :D

---

