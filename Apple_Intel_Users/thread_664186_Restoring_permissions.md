---
title: "Restoring permissions"
date: 2008-01-10
forum: Apple Intel Users
---

### Post by omax on 2008-01-10
Hi! I'm having some troubles with my Tiger installation.

I dualboot OSX and xubuntu, and from linux I mounted my HFS-partition, though since I couldnt access some folders (like /Users/login/Desktop/ I changed the permissions on it from linux by:
sudo chown linuxuser /media/OSX/Users/login/Desktop
+ eventually
sudo chown linuxuser /media/OSX/*

When I rebooted in to osx my dock was not my configured one, and I couldnt see my folders on Desktop, and further I couldnt access Desktop due to permissions.

I entered Partition Manager and tried to repair permissions, it said it was sucessfull but I do not notice any difference. Is there a way to fix this before I reinstall Macosx again?

Happy to hear from you!
omax

---

### Post by omax on 2008-01-11
SOLVED

```

chown 501 /media/OSX/Users/login/*
```

---

### Post by cyberdork33 on 2008-01-11
> **omax said:**
> SOLVED

```

chown 501 /media/OSX/Users/login/*
```

You could have booted OSX, logged in as root (administrator) and did the same command methods that you did in linux:
```
sudo chown osxuser /media/OSX/Users/login/Desktop
sudo chown osxuser /media/OSX/*
```
Changing ownership of files is not the same as changing permissions... you use the chmod command to alter permissions, and the chown command alters ownership.

---

