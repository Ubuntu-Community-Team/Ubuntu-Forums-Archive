---
title: "proftpd wont work all of the sudden? :("
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Stomstedt on 2006-10-20
owner@owner-desktop:~$ sudo proftpd start

Please provide passphrases for these encrypted certificate keys:
RSA key for the 0.0.0.0:1980 (Lovepad) server:
Verifying - RSA key for the 0.0.0.0:1980 (Lovepad) server:
owner-desktop - mod_delay/0.4: error opening DelayTable '/var/run/proftpd/proftpd.delay': No such file or directory


Why won't this work? It used to but now not...

and now also when I type ls var/run/proftpd there is no such file or directory.. it was working a couple days ago...

---

### Post by taurus on 2006-10-20
Shouldn't it be /var/run/proftpd instead of var/run/proftpd???

---

### Post by Stomstedt on 2006-10-20
Yeah, that's what I meant, sorry.

---

### Post by taurus on 2006-10-20
I guess it is looking for /var/run/proftpd/proftpd.delay and since you don't have it, it wouldn't start.  However, I believe the command to start it from a terminal is

```
sudo /etc/init.d/proftpd start
```
Otherwise, try to remove it and reinstall it again with aptitude...

---

