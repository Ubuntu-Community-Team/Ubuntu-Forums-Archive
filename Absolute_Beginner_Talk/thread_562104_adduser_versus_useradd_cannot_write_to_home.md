---
title: "adduser versus useradd /cannot write to home?"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2007-09-28
I was using the command useradd, until I found out about adduser, which automatically created home folder and asked me a few questions, the problem is that it seems that the person cannot write to their home folder.  When I did useradd the person could read/write to the directory.

How do I give a user 100% access  to their home directory for both reading/writing?

---

### Post by Buffalo Soldier on 2007-09-28
Try checking your **/etc/adduser.conf** file. Look for this section:

```
# If DIR_MODE is set, directories will be created with the specified
# mode. Otherwise the default mode 0755 will be used.
DIR_MODE=0755
```

---

### Post by bruce89 on 2007-09-28
```
sudo chown -R user:user /home/user
```

Replace user with the user name.

---

### Post by bone2006 on 2007-09-28
thanks bruce89  that did the trick

I think the problem was that I created the user, then created folders in the user's directory with sudo.  The person could read and write in their own home directory I just found out, but the folders I created with sudo could only work with root user.

But everything is working with the command you posted

Thanks

---

