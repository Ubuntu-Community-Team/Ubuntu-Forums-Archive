---
title: "Permissions Issues"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by dahlberg123 on 2008-02-04
I am fairly new to this Ubuntu world so please bare with me.  I understand some of the concepts but the only one that really troubles me still is permissions.  So I've installed MySQL, Apache, PHP and Quanta but they are all useless to me as I am unable to write or edit files in the /var/www/ DIR.  There are so many tutorials and snippets of information out there permissions I don't even know where to start.

Permissions issues is the only thing that is holding me up on moving completely over to linux so please help!

Thanks in advance,

Tom

---

### Post by bodhi.zazen on 2008-02-04
permissions take a while to get adjusted to.

See these links :

 [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

	[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)


also, to get root access use sudo :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)


Or you can use:

```
gksu nautilus
``` if you prefer a graphical interface.

---

### Post by mikewhatever on 2008-02-04
Very easy question, read this and you are done -->[http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions).

---

### Post by dahlberg123 on 2008-02-04
Yes, permissions is by far the hardest thing to learn when starting out with linux; for me at least.  Thanks everyone for the help; hopefully after a little "light" reading I should be good to go.

Thanks,

Tom

---

