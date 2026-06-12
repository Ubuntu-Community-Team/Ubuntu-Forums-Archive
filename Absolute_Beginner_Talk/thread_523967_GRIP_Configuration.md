---
title: "GRIP Configuration"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by ashkev on 2007-08-12
I have installed grip and configured it to use lame to encode MP3's.  My problem is that every time I rip, I have to tell it where lame is located... /usr/bin/lame under config > encode > encoder executable.  How can I save this so I don't have to re-enter it each time?

Thanks

---

### Post by schorsch on 2007-08-12
When you are in a terminal session in your home directory please do:

```
pwd
ls -l .grip
grep lame .grip
whoami
```

and post the output here.

---

### Post by ashkev on 2007-08-12
IT seems to be working fine now....not sure why....but here is the output you asked for.


kevin@edubuntu:~$ pwd
/home/kevin
kevin@edubuntu:~$ ls -l .grip
-rw-r--r-- 1 kevin kevin 1475 2007-08-12 18:56 .grip
kevin@edubuntu:~$ grep lame .grip
mp3exename /usr/bin/lame
kevin@edubuntu:~$ whoami
kevin
kevin@edubuntu:~$

---

