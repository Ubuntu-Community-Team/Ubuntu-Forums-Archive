---
title: "Virtual box status code 38"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by avanrens on 2007-08-06
I have had Virtual box running but it has just stopped on me with a dialog box with the following;

Cannot open host device '/dev/hdg' for readonly access. Check the permissions of that device ('/bin/ls -l /dev/hdg'): Most probably you need to be member of the device group. Make sure that you logout/login after changing the group settings of the current user.
VBox status code: -38 (VERR_ACCESS_DENIE

---

### Post by felicity on 2007-08-06
Did you add your user account to the vboxusers group in the System > Administration > Users and Groups menu?

---

### Post by avanrens on 2007-08-06
Thank you so much you are a life saver that worked.

---

### Post by RedWagon on 2008-06-16
I'm having a similar problem, only with a com port.  I changed the permissions to this:

lakeview@Server:~$ /bin/ls -l /dev/port
crwxrwxrwx 1 root kmem 1, 4 2008-06-12 22:47 /dev/port

then went under System > Users and Groups > Manage Groups > vboxusers > Properties > then checked root and Lakeview (the only two users in the list) and I still get the status code -38 when I try to boot.

---

