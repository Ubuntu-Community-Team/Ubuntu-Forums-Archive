---
title: "lost my login and password"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by twbdan on 2007-10-21
I jsut completed installing the new upgrade of 7.10, added my samba and inetd  and all extensions.  The computer ask me for a reboot.  When the logon screen appears it wont let me login under my login name and password. Help:popcorn:

---

### Post by bodhi.zazen on 2007-10-21
Boot to recovery mode

You will be loged in as root

Enter ```
passwd <user>
```

where <user> = the user you want to set a passowrd

Then enter :

```
telinit 2
```

---

### Post by myCharlie on 2007-10-24
I have the same problem. How do I boot into recovery mode?

---

### Post by Dr Small on 2007-10-24
> **myCharlie said:**
> I have the same problem. How do I boot into recovery mode?
You boot in recovery mode from GNU GRUB, the bootloader.
If you do not see GRUB, where you can choose Recovery Mode, press Escape at bootup, (continually) until GRUB launches.

Dr Small

---

