---
title: "defining rights for a group"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by pkj on 2007-08-09
I have created a new group (with one user).

How do i define the rights for this group...

Specifically i do not want the users of this group to be able to use USB drives.....

Suggestions !!!!!!!!!!!!!!

pkj

---

### Post by Dr Small on 2007-08-09
System > Administration > Users and Groups > [select the user] > Properties > User Privileges > [uncheck] Enable access to external storage devices automatically

Dr Small

---

### Post by oilchangeguy on 2007-08-09
go to system, admin, users and groups. highlight the user or group, properties, user priv. don't see an option for usb (in version 6.06). there is an option for external devices, however.

---

### Post by pkj on 2007-08-09
Tried all this but dosen't seem to be working

pkj

---

### Post by oilchangeguy on 2007-08-09
> **pkj said:**
> Tried all this but dosen't seem to be working

pkj

you may need to reboot.

---

### Post by Dr Small on 2007-08-09
Once you have set the permissions for that user, you will need to logout and log back in, in order for it to work.

Dr Small

---

### Post by aseem on 2007-09-01
Same question, but on a Ubuntu server.

How can I set group rights on an uBuntu server without the graphical UI, and specifically, how can i give a user administrative rights?

---

### Post by aseem on 2007-09-01
SOLVED:

Sorry, I should have read some more before posting.  

For the record:  There is a file /etc/group.  Edit this file, and place the your username as member of the group "admin".  This will give your user admin rights.

---

