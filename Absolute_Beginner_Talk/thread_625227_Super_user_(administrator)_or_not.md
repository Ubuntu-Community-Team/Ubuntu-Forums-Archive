---
title: "Super user (administrator) or not?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-11-27
Can someone tell me how to tell if a logged on account on Ubuntu is a Super user account or a restricted user account? How do you set up a restricted account? How many user levels are available?

---

### Post by st33med on 2007-11-27
There is no root or super admin account. To have super user privileges in Ubuntu, just run sudo in any command.

---

### Post by bodhi.zazen on 2007-11-27
Anyone in the admin group can sudo, or run a command as root.

For a "non-privilaged" account, make a new user and do not put the user in the admin group or modify /etc/sudoers (with the command visudo)

Use gksu or graphical apps

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

	gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by fmbugdadi on 2007-11-27
Thanks for the info guys...

---

