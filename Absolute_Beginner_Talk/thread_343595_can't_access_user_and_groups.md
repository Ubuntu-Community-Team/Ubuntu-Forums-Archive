---
title: "can't access user and groups"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2007-01-21
went to system->adminstration->user and groups
typed the password and it won't allow me access to it
here is the error i'm getting

The configuration could not be loaded

You are not allowed to access the system configuration

---

### Post by taurus on 2007-01-21
What's the output of this command from a terminal?

```
id
```

---

### Post by lime4x4 on 2007-01-21
john@john-edgy:~$ id
uid=1000(john) gid=1000(john) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),1000(john)
john@john-edgy:~$

---

### Post by taurus on 2007-01-21
And any problem running this command?

```
sudo apt-get update
```

What are you trying to do with the User & Group in System -> Administration anyway?

---

### Post by lime4x4 on 2007-01-21
that works just find

this what i need to do

When you installed VirtualBox, it created a group called vboxusers. For whatever reason, the installer was unable to automatically add you to the group, so you will have to do it yourself.

However, as promised, no shell.

Go to System -> Administration -> Users and Groups. On the right, you will see a button labeled "Manage Groups." Click on it. Scroll down the list to "vboxusers." The last item for me. Double click on it. You will see a list of users. Check your name, and press "OK." Then close "Groups settings." Then close "Users settings."

---

### Post by taurus on 2007-01-21
```
sudo adduser **username** vboxusers
```
Where **username** is your actual login name.

---

