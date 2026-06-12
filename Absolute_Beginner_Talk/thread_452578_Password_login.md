---
title: "Password login"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Xpretender on 2007-05-23
I have forgetten my login username, any ideas?

---

### Post by aysiu on 2007-05-23
Boot into recovery mode and type ```
cd /home
ls
``` You should see your username in the list. If you've also forgotten your password, type ```
passwd *username*
``` where *username* is your username, and then ```
reboot
```

---

