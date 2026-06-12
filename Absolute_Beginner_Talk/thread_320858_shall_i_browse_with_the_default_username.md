---
title: "shall i browse with the default username ?"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by tony2 on 2006-12-18
When I installed Ubuntu it asked to provide a username. I gave my real name and a password. I donot know this is the admin name or not. Can I browse the internet using this name and password or shall i create a new user account so that it shall be safe on the net?

---

### Post by jordanmthomas on 2006-12-18
This is not the admin account and is suitable for web browsing.
The admin account is root and to use it you need to prepend sudo to any command you run.  (at least in the default setup)

Don't worry about viruses, basically.

---

### Post by tony2 on 2006-12-18
thnx jordan

---

### Post by aysiu on 2006-12-18
Just to offer a bit more explanation:
Your username belongs to a group called *admin*. Anyone in that group almost always has limited privileges. With *sudo* and password authentication, a user in the *admin* group is allowed to temporarily assume root privileges (allowing this user to modify system files). That privilege escalation is only temporary.

More info here:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by tony2 on 2006-12-18
thanks for the clarification.

---

