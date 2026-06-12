---
title: "How can I change what is seen when someone logs in via ssh?"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-03-12
Right now it says something like (copy pasted from elsewhere)...
```
$ ssh -X lumen
Viimeinen kirjautuminen: pe loka 26 22:07:06 EEST 2007 koneelta yonix.lan päätteellä pts/0
Linux lumen 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
$
```

how can I change it to be crazy ascii art or something like that?

---

### Post by justleen on 2008-03-12
in your /etc/ssh/sshd.config is a line
```

Banner /etc/issue.net

```
This is your banner. In my case, it displays the file "/etc/issue.net"

---

