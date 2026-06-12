---
title: "USB device permissions"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by ljpenton on 2008-02-05
Hello,

I have a USB POS receipt printer I'm attaching to my Gutsy system. When powered on the printer is added as /dev/usb/lp0 with permissions of:

crw-rw---- 1 root lp   180,  0 2008-02-05 10:11 lp0

I need to send POS escape commands directly to the printer, so need to set the permissions to rw-rw-rw-. Is there a way I can have the permissions configure this way when it is powered on? I don't want to have my cashiers execute sudo chmod every morning.

---

### Post by spiderbatdad on 2008-02-05
In /etc/fstab, I believe you want to set option umask=000

---

### Post by ljpenton on 2008-02-06
Thanks for the info. Couldn't find any documentation on the web on adding a printer to /etc/fstab (everything I found says this is for mounting files systems).

Got around the problem by adding the login userid to the "lp" group by manually editing /etc/groups (couldn't add the user to the group via Admin/Users and Groups for some reason).

---

