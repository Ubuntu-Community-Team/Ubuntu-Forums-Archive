---
title: "Can't sudo and can't log in as root"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by gpaciga on 2007-02-16
I did a stupid thing. I was trying to add my user to a new group, but the command I used seems to have removed myself from all other groups as well.

Now, I can no longer do sudo. I suspect this is because I was removed from the group of sudoers (I think it was called 'admin').

For some reason, on a tty, I can't even log in directly as root, getting a login incorrect error, even though I know the password.

How can I give my user permission to do sudo again without root priviledges?

---

### Post by taurus on 2007-02-16
Boot into recovery mode from GRUB menu and add your login name to groups adm and admin in /etc/group.

```
nano -B /etc/group
```
Exit with <Ctrl>x and answer the question with Y and Return.

---

