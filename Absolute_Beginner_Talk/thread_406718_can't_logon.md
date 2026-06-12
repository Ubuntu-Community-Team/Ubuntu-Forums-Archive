---
title: "can't logon"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by TEDNUGNT on 2007-04-11
i have edgy 6.10 (single boot, no windows) installed on a dell inspiron 8100.

last night while in 'gnome' i beleive (on the desktop) i clicked on 'users' under the system menu and changed my username and password.

i have since logged off, restarted the system, and im now trying to log back in but i cant. it wont recognize neither my new username/password combo nor my old one.

what did i do? how can i recover?

i realized that perhaps this wasn't the best way to try to change either my username and password.

help! thanks.

---

### Post by taurus on 2007-04-11
Boot into recovery mode from GRUB menu and see what is your username name now.  Then, try to change the password for it again.

```
ls -la /home
passwd **john**
```
Assuming john is the name username now...

---

### Post by TEDNUGNT on 2007-04-11
thanks that did the trick

---

### Post by nsilva on 2007-04-11
> **taurus said:**
> Boot into recovery mode from GRUB menu and see what is your username name now.  Then, try to change the password for it again.

```
ls -la /home
passwd **john**
```
Assuming john is the name username now...
That could be a serious security problem, specially with Ubuntu that by default the user has sudo privileges. How could I restrict this.

---

### Post by taurus on 2007-04-11
> **nsilva said:**
> That could be a serious security problem, specially with Ubuntu that by default the user has sudo privileges. How could I restrict this.

Just don't add that user to groups adm and admin in /etc/group.  Then, that user can't use sudo/gksudo.

---

### Post by ComplexNumber on 2007-04-11
> **nsilva said:**
> That could be a serious security problem, specially with Ubuntu that by default the user has sudo privileges. How could I restrict this.
set up a password for grub. someone else may know the details, but i've never tried. i know its possible though.

EDIT: looks like you, taurus, got there before me with the more elegant solution :mrgreen:

---

