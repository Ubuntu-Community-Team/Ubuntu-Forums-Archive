---
title: "[SOLVED] How do I capture the text when booting?"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by kentl on 2007-11-03
Hi,

I've installed a command-line system using the alternate installer for the desktop version of Gutsy. There are a few error messages that flies by before I'm able to log into the system. My question is.

How do I capture these error messages? As I would like to discuss them on this forum.

---

### Post by Cannaregio on 2007-11-03
Those messages are already logged and captured.
Try for instance
```
dmesg  | less
```

and also of course system --> administration --> system log

there are many more logs; depends what kind of info you seek
have a look inside /var/log and, in your case, once there,

```
cat boot | less
```

---

### Post by kentl on 2007-11-03
Thank you!

---

### Post by Cannaregio on 2007-11-05
Glad it worked.
Please modify your header adding 
```
SOLVED:
```

---

### Post by kentl on 2007-11-06
All right, done. :-)

---

