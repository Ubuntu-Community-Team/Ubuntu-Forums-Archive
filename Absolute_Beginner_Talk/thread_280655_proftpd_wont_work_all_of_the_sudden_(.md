---
title: "proftpd wont work all of the sudden? :("
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Stomstedt on 2006-10-19
owner@owner-desktop:~$ sudo proftpd start

Please provide passphrases for these encrypted certificate keys:
RSA key for the 0.0.0.0:1980 (Lovepad) server:
Verifying - RSA key for the 0.0.0.0:1980 (Lovepad) server:
owner-desktop - mod_delay/0.4: error opening DelayTable '/var/run/proftpd/proftpd.delay': No such file or directory


Why won't this work? It used to but now not...

---

### Post by taurus on 2006-10-19
I guess the obvious question is do you have /var/run/proftpd/proftpd.delay?

```
ls -la /var/run/proftpd/proftpd.delay
```

---

### Post by Stomstedt on 2006-10-19
No such file or directory

---

