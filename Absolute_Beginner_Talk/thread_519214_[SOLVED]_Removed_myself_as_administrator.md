---
title: "[SOLVED] Removed myself as administrator"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-08-06
Hi,

I unticked administrator in my user account and now I can't run synaptic package manager. How do I add myself back? I tried to log in as root on switch user but it wouldn't let me.

Thanks

---

### Post by Dr Small on 2007-08-06
Did you try "gksudo users-admin" and then make your user account an administrator again?

---

### Post by Rocket2DMn on 2007-08-06
You will need to boot in recovery mode to re-enable yourself as administrator.  This will log you log you in as root.

---

### Post by keymoo on 2007-08-06
Thanks for the quick reply. I tried that command and then tried to go to users and groups but nothing happened.

---

### Post by keymoo on 2007-08-06
Thanks for the quick reply. I rebooted in recovery mode and i got to the command line. I'm not sure what to type there.

I did do this:
usermod -a -G root keymoo

but when i log back in, most of the Administration menu in Ubuntu GUI has now disappeared. What's happened? How do I add myself back as admin? Thanks.

---

### Post by bodhi.zazen on 2007-08-06
Boot to recovery mode

use nano :

nano /etc/groups

Add your user to the admin group (after root, comma delineated)

Ctrl-X to exit, type "Y" to save, reboot

---

### Post by Rocket2DMn on 2007-08-06
Can you start the GUI from recovery mode?
```
startx
```
If you can get to the GUI you should be able to access the settings from there.
edit: listen to b.z, he's the bombsack.

---

### Post by aysiu on 2007-08-06
In recovery mode: ```
adduser *username* admin
``` should do it. For more details:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by keymoo on 2007-08-06
You guys are great. All sorted. :)

---

