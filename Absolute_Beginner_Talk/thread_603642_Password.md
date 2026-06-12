---
title: "Password"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by kvnm on 2007-11-05
Hello

 I have forgotten my username, and password on my home PC,and cannot login.
 What can I do to retrieve it?

---

### Post by aysiu on 2007-11-05
Reboot into recovery mode (it's the second boot option in the boot menu).

Type ```
cd /home
ls
``` Your username should be displayed in the results. Then, type ```
passwd *username*
``` to reset the password for *username* (whatever the actual username is). Finally ```
sudo shutdown -r now
```

---

### Post by kvonb on 2007-11-05
-

---

