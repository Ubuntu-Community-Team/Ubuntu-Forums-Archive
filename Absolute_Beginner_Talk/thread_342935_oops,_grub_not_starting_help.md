---
title: "oops, grub not starting help"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2007-01-20
computer froze while updating for the first time and now when i get to the login screen and enter my password and log in it just freezes. what do i do?

---

### Post by bodhi.zazen on 2007-01-20
> **da1nonlymikeo said:**
> computer froze while updating for the first time and now when i get to the login screen and enter my password and log in it just freezes. what do i do?

Well, if you get to the login screen it is not a grub problem ;)

Try booting in recovery mode. This will log you into the CLI as root ....

See if you can finish the update:

```
aptitude update
aptitude upgrade
```

Error message ??

If not, type ```
startx
``` and post any error messages.

If none, reboot :p

---

