---
title: "sudo: /etc/sudoers is owned by uid 1000, should be 0"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Faaron on 2007-04-01
I was following this guide [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.htm]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html")l in order to access a WPA network. Unfortunately, I kept receiving "sudo: /etc/sudoers is owned by uid 1000, should be 0 " once I made it to **sudo touch /etc/default/wpasupplicant**. I have no idea what happened, I would really appreciate an explanation/solution. Thanks.

p.s. I'm using Edgy 6.10, Dell Inspiron E1505 if it's relevant.

---

### Post by Bachstelze on 2007-04-01
Boot in recovery mode and do :

```
chown root:root /etc/sudoers
chmod 440 /etc/sudoers
reboot
```

---

