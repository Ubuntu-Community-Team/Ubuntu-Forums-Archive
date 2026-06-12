---
title: "Authorization problem"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Alkor on 2006-07-08
I just installed Kubuntu 6.06 and everything runs much better than I expected .  However I am having problem with authorizing myself as root in terminal.
Here is what I get.
```
su
Password:
su: Authentication failure
Sorry.

```

The strange thing is that if I enter "sudo su" everything works fine, sometimes it even does not ask to enter password.
So, what is a problem here?

Thanks

---

### Post by aysiu on 2006-07-08
There is no enabled root account by default.

[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by GStubbs43 on 2006-07-08
Try
```
su UserName
``` instead of just ```
su
```
Where UserName is obviously, your username:D

---

