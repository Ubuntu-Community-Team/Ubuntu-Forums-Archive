---
title: "[SOLVED] Permissions error on login"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-08-26
Hi when I log in I get this message:
[I]User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.
[/I]
I tried the following:
```
sudo chmod 644 .dmrc
chown keymoo keymoo
```Permissions on .dmrc:
```
-rw-r--r-- 1 keymoo keymoo 26 2007-08-09 22:35 .dmrc
```Permissions on my HOME directory:
```
drwxrwxr-- 74 keymoo keymoo  4096 2007-08-26 22:11 keymoo
```I still get the error. Ideas?

Thanks.

---

### Post by kellemes on 2007-08-26
Sorry for asking the obvious but.. did you already logout and login again?

---

### Post by Dr Small on 2007-08-26
Chmod your home folder to 755, and .dmrc to 644 and see if that helps.

Dr Small

---

### Post by keymoo on 2007-08-26
> **kellemes said:**
> Sorry for asking the obvious but.. did you already logout and login again?


:) Yeah I rebooted actually.

---

### Post by keymoo on 2007-08-26
> **Dr Small said:**
> Chmod your home folder to 755, and .dmrc to 644 and see if that helps.

Dr Small



Thanks, solved - maybe the 755 was the issue. Cheers!

---

### Post by Dr Small on 2007-08-26
I've messed with this same thing before several times and even locked myself out of the desktop by putting the wrong permissions on the home folder. I had to login to the command line and chmod the directory again to get back in.

Dr Small

---

