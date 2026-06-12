---
title: "what that error means ?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by black_ice on 2007-03-31
hello all when i running some programs by the shell i got that error 

[PHP] root@adam-laptop:~# mysql-query-browser 

(mysql-query-browser:7835): Gtk-WARNING **: cannot open display: [/PHP]

---

### Post by taurus on 2007-03-31
You can't open a GUI if you log in as root from your regular account.  Instead of logging in as root, try to run this command from your regular account.

```
gksudo mysql-query-browser
```

---

