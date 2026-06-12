---
title: "Superuser in Terminal"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-19
Can someone tell me how to become superuser in terminal, I have an error that requires me to manually run ;dpkg --configue -a' , and I would like to try and fix it.

Thanks,
-c.

---

### Post by Jussi Kukkonen on 2006-10-19
for that one command:
```
sudo dpkg --configure -a
```

---

### Post by HereInOz on 2006-10-19
Type sudo and then the command.

You will be asked for your password - it is the same one that you use to log on.  You will then have su rights for a short while.

The root user is disabled deliberately in Ubuntu.  Use sudo instead.

Cheers.

---

### Post by Crooksey on 2006-10-19
Menu > System Tools > Root Terminal

---

