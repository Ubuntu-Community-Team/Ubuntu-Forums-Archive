---
title: "A lot of sources.list and can't be deleted"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by coconeco on 2007-04-23
Hello.  I need your help!

It seems I have made several sources.list files and some of them can not be accessed by myself. :( 

> file:///etc/apt/apt.conf.d
file:///etc/apt/secring.gpg
file:///etc/apt/sources.list
file:///etc/apt/sources.list.d
file:///etc/apt/sources.list.orig
file:///etc/apt/sources.list.save
file:///etc/apt/sources.list.save.1
file:///etc/apt/sources.list.save.2
file:///etc/apt/sources.list.save.3
file:///etc/apt/sources.list.save.4
file:///etc/apt/sources.list_backup
file:///etc/apt/trustdb.gpg
file:///etc/apt/trusted.gpg
file:///etc/apt/trusted.gpg~


What can I do? And if you noticed anything wrong, give me some advice..

coco

---

### Post by nanotube on 2007-04-23
well, first of all, a few backups never hurt anybody, so unless these are really bothering you, just leave them be. :)

second, they're probably owned by root, so if you want to delete them, you have to sudo. easiest way is to just start a file manager as root, and then browse over to /etc and delete those extras. to start a root file manager, run command
```
gksudo nautilus
```

hope that helps.

---

### Post by mills on 2007-04-23
"gksudo nautilus" will give you the permission to do it

---

### Post by Motoxrdude on 2007-04-23
> **coconeco said:**
> Hello.  I need your help!

It seems I have made several sources.list files and some of them can not be accessed by myself. :( 



What can I do? And if you noticed anything wrong, give me some advice..

coco

```
cd /etc/apt
sudo cp sources.list backup.backup
sudo rm sources.list*
sudo cp backup.backup sources.list
sudo rm backup.backup
```

Copy and paste that into the terminal.

---

### Post by coconeco on 2007-04-23
Thank you for the quick reply, nanotube, mills and Motoxrdude.  

> file:///etc/apt/apt.conf.d
file:///etc/apt/secring.gpg
file:///etc/apt/sources.list
file:///etc/apt/sources.list.d
file:///etc/apt/trustdb.gpg
file:///etc/apt/trusted.gpg
file:///etc/apt/trusted.gpg~


I could it finally!  Thank you...

coco

---

