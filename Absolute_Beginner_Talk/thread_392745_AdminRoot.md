---
title: "Admin/Root"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by puppyfarts on 2007-03-24
So I just installed Ubuntu (awesome, right?), and I'm a little confused about the admin account.

When I open terminal and type in sudo passwd, I get this:
Password:
Enter new UNIX password:

Is the UNIX password the admin account password?
I don't think I'm logged in as admin (pwd gives home/my name), but I don't know.

---

### Post by aysiu on 2007-03-24
Did you do an OEM install? It sounds as if it's asking you for your password in order to change your password to a new one.

---

### Post by lamalex on 2007-03-24
sudo passwd changes your user account password, 
```

sudo su
passwd

```
will change root password

---

### Post by puppyfarts on 2007-03-24
Cool.  Thanks.

---

