---
title: "Problem deleting user with userdel"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by misterpms on 2007-01-10
I am having a problem with removing users. I have executed the following command:
```

sudo userdel -r <username>

```

but the user still has a directory in /home. I tried executing the userdel command again but I get the following error: 
> 
userdel: user <username>/ does not exist


I have had a look at the /etc/passwd and /etc/group files and <username> no longer exists in either of them. However, <username> still has entries in the /etc/passwd- and /etc/group- files. Is this the reason behind the recalcitrant /home/<username> ? Also, what are the *- files in /etc ?

---

### Post by scrooge_74 on 2007-01-10
the user directory will remain that is normal, just do sudo -rf /home/username

---

### Post by misterpms on 2007-01-11
Problem resolved. Thanks!

---

