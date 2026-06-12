---
title: "/usr/bin no access allowed"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by iancvt55 on 2008-01-05
Hi

I'm trying to copy a file into /usr/bin and keep getting a message I don't have permissions.

I installed Ubuntu onto the PC and am the only user.

Don't want to go back to XP this early on but it's doing my head in

Thanks

Ian

---

### Post by kellemes on 2008-01-05
You need to be root, so start nautilus (filemanager) as root like so..
from terminal...
```
gksudo nautilus
```


from terminal you can also copy files like so..
```
sudo cp /frompath/files /topath/
```

---

### Post by t0p on 2008-01-05
You'll need to switch to superuser - ie type "sudo" in front of the command you wish to use.

---

### Post by Abu_Dayya on 2008-01-05
Type in terminal

```
gksudo nautilus
```
This should open the file browser in root mode

---

### Post by iancvt55 on 2008-01-05
Thanks everybody, moving on slowly

---

### Post by kellemes on 2008-01-05
> **iancvt55 said:**
> Thanks everybody, moving on slowly


Just keep moving.. you'll be there in no time. :popcorn:

---

