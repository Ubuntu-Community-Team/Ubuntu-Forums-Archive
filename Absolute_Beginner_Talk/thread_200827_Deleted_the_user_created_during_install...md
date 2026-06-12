---
title: "Deleted the user created during install.."
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by nitin_mz on 2006-06-20
I created a new user with sudo permissions, and then deleted the original user created during dapper install.

As a result, I started seeing "broken pipe" error messages running sudo.

Thankfully, I had set a root passwd, and was able to "su" and then fix /etc/passwd, /etc/sudoers, /etc/groups to give permissions to the new user.

Now System -> Administration on the desktop no longer lists the users/groups manager, or the synaptics package manager. Is there a way to restore the admin menus?

---

### Post by nitin_mz on 2006-06-21
bump.. last attempt before i go about reinstalling

---

### Post by catlett on 2006-06-21
[http://doc.gwos.org/index.php/DapperGuide#How_to_allow_more_sudoers](http://doc.gwos.org/index.php/DapperGuide#How_to_allow_more_sudoers) Check this guide and see if there is anything here you didn't do. One thing I noticed that might be it. Did you add the new sudoer to the "admin group"?

---

### Post by rai4shu2 on 2006-06-21
You may only need to reinstall gnome-system-tools and synaptic if you do need to install.

---

### Post by nitin_mz on 2006-06-21
Thanks catlett and rai4shu2

---

