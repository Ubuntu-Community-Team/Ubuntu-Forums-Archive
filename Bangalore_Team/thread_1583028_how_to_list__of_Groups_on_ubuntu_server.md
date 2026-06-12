---
title: "how to list  of Groups on ubuntu server"
date: 2010-09-27
forum: Bangalore Team
---

### Post by vaibhavsd on 2010-09-27
how to list  of Groups on ubuntu server,


and  how  to create user on ubuntu server

---

### Post by quixote on 2010-09-29
```
cat /etc/group
```will list all the groups, including ones used only by the system.  Just typing ```
groups
```will list all the groups of which the current user is a member. To add a user use ```
sudo useradd *name*
``` To add a user to a specific group use ```
sudo usermod -G *name-of-group* -a '*name-of-user*'
```

For more information on all these -- and it's really a good idea to make sure you know what you're doing before doing system-level commands -- you can type ```
info *command-name*
``` or ```
man *command-name*
``` For instance "man useradd".

---

### Post by toofun on 2012-09-20
I did this without adding the -a option so now I no longer have root access, and oddly enough the admin group is no longer in the /etc/group file. Does anyone know how to recover from such a scenario?   The link:
[http://ccollins.wordpress.com/2007/07/02/restore-default-ubuntu-groups/](http://ccollins.wordpress.com/2007/07/02/restore-default-ubuntu-groups/)

talks about a similar situation but does not talk about how to add the admin group back into the /etc/group file. It's easy to edit back in but what number do you assign it?

---

### Post by matt_symes on 2012-09-20
This is a really old thread. Closed. Please start a new thread.

---

