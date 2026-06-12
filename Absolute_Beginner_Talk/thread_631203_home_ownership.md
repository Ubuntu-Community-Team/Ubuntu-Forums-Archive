---
title: "/home ownership"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-12-04
For some odd reason, my /home partition is owned by root and when I boot as a user <Tony> i get an error that the system cannot write to /home. So I boot in as root amend the ownership to allow all users to write to it  and reboot as a user and all is well. When I reboot the same happens.

How do I change ownership of /home which resides on /dev/sda2 to tony (which is my user name?


tchoklat

---

### Post by PmDematagoda on 2007-12-04
Try:-

```
sudo chown -hR tony /home/tony
```

Assuming tony is your username.

---

