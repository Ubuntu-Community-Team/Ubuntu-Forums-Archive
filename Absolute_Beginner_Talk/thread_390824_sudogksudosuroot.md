---
title: "sudo/gksudo/su/root"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by acmethunder on 2007-03-22
After using Ubuntu for about 6 months, there are still a couple things that I don't get, the main one being the differences between sudo, su, gksudo, root.

As I understand it, root gives me access to everything and I don't use it unless its needed.

But what about the other three...I have tried poking around different sites (Ubuntu and others), but there isn't really anything that fully explains them...such as what exactly they mean, and how I would when to use them.

Thanks, and good job with the all the different ways to get help, please keep it up...much better than my previous OS.

---

### Post by Bachstelze on 2007-03-22
*sudo* lets you run a command as if you were another user - not necessarily root.

*su* stands for *switch user* and as it's name says, "switch" you to another user - once again, not necessarily root - in a terminal.

gksudo and gksu do the same thing but for GUI apps - they will popup a window asking for the password instead of prompting in the terminal.

---

### Post by dreadlord_chris on 2007-03-22
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2007-03-22
*su* will allow you to switch users. If you don't specify a user, that user will be root.

Ubuntu disallows traditional root logins by default (recovery mode being the only exception). You can enable a root login by setting a password for root. This is completely unnecessary.

*sudo* allows a regular user in the *admin* group to temporarily assume root-like privileges for some tasks.

*gksudo* is the graphical version of *sudo*

More details here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

