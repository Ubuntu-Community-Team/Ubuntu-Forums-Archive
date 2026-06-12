---
title: "User/Pass Reset?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by tpauth on 2008-02-04
I just installed Ubuntu on my third system in the last week. Everything's going great. But, I got to the login screen on this lastest install, and I must've typed in something wrong with my username/password during the setup and can't get in.

As suggested by someone on the IRC  channel, I went into single-user Recovery mode, but that's as far as I've gone, as I'm not familiar with too many linux commands. Can someone point me to a way to get my login reset?

Thanks!

---

### Post by spiderbatdad on 2008-02-04
this was just covered by another thread:)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Dr Small on 2008-02-04
To find the account username, run:
```
ls /home
```

Then to reset the password:
```
passwd *user*
```

---

