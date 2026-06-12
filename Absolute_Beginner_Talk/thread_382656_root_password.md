---
title: "root password"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by janderson on 2007-03-12
Pardon me if this has been asked before (I searched and couldn't find it)...

What is the default root password?  When I "su" from a shell, all the passwords I tried don't work (my normal login password, "root" and <blank>).  

I know I read that you can preface commands with "sudo" to run as administrator but can't you just login as root?  I have many years experience with UNIX systems and have always been able to login and work as root.

Thanks,

John Anderson

---

### Post by 23meg on 2007-03-12
The root account is disabled by default.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by taurus on 2007-03-12
If you really want to log in as root, then you need to create a password for it first.

```
sudo passwd root
```
Then, log in as root with

```
su -
```

---

### Post by Bachstelze on 2007-03-12
Though I really can't see any reson why one would want to login as root... Well, actually I do but it's nothing a beginner would have any use for. Why not just get a root shell with *sudo -i* ?

---

### Post by janderson on 2007-03-12
Thanks!  I knew it had to be something simple.

John

---

