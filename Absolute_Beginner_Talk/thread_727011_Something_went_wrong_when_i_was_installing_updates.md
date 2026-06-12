---
title: "Something went wrong when i was installing updates..."
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Kaimaru on 2008-03-17
I was installing updates and watching the details just for fun and my son ran by and started pushing buttons on the computer. It quit installing and now when i click install updates it give the error.....

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So i opened up the command line and typed dpkg --configure -a but it tells me "dpkg: requested operation requires superuser privilege" soooo i went into users and made shure im an admin which i am and i still cant get it to run.... im very very new to linux so please let me know what im doing wrong. Thanks!

---

### Post by taurus on 2008-03-17
Just put a sudo in front of the command.

```
**sudo** dpkg --configure -a
sudo apt-get update
```

---

### Post by Arthur Archnix on 2008-03-17
prefix the command with sudo

EDIT: Taurus is quick.

---

### Post by Anicka on 2008-03-17
Try: sudo dpkg --configure -a
sudo means "run with admin privileges"

Edit: Yes, he is quick, very quick

---

### Post by Kaimaru on 2008-03-17
Thanks guys. He is very quick!! But you guys were really fast aswell Thanks to you all for your support!

---

