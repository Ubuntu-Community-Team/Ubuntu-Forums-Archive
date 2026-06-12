---
title: "user permissions"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by dernier_recours on 2006-04-16
Hi,

I would like to give root permissions to a user. The user don't get root privileges even though his primary group is "root". What should I do?

Thanks!

---

### Post by taurus on 2006-04-16
If you want a user to be able to run command as root using sudo, that user needs to belong to group "adm" (or admin) in /etc/group.  It won't work if you add that user to group root!

---

### Post by aysiu on 2006-04-16
Let's say your user is named *user*.

In Gnome, go to System > Administration > Users and Groups, click on *user* and add her to the group *admin*

In KDE, go to KMenu > System > KUser and do the same.

---

### Post by dernier_recours on 2006-04-16
In fact, I would like to give the user the permissions for full access to everything. The user can't copy files into /usr/share (even though he belongs to the admin group). Moreover, the user can't run xampp (terminal /opt/lampp/lampp start).

---

### Post by aysiu on 2006-04-16
Any user in the admin group can copy to /usr/share

In Gnome, Alt-F2 ```
gksudo nautilus
``` and go to /usr/share
In KDE, Alt-F2 ```
kdesu konqueror
``` and go to /usr/share
In the terminal ```
cp /path/filename /usr/share/filename
```

---

### Post by 5-HT on 2006-04-16
[quote=dernier_recours]In fact, I would like to give the user the permissions for full access to everything. The user can't copy files into /usr/share (even though he belongs to the admin group). Moreover, the user can't run xampp (terminal /opt/lampp/lampp start).[/quote] If the user is in the admin or adm groups (depending on which one exists), prefacing a comman with 'sudo' will run the command under root privileges.

e.g., ```
 sudo cp foo /usr/share/ 
``` 
HTH

---

