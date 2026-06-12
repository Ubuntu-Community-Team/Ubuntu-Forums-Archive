---
title: "ssh monitor"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by magicman5421 on 2008-03-30
ok so i recently installed a ssh server on my home computer. I'm using it to connect to from school and browse the web. I've also made accounts for a few other people at my school, and i'm getting $1 a month from them for the connection. Is there any way to monitor (through a log file or otherwise):
a) when they log on
b) from where (ip address)
c) web traffic that flows through the tunnel through their account
d) when they log out
First two are a main priority, second 2 i would like, if possible
Also, is there any way to make an account not be able to be logged in from more than one place at the same time? as in if someone is already logged in with that account and someone else tries to log in with it for them to get an error?

---

### Post by magicman5421 on 2008-03-30
bump

---

### Post by magicman5421 on 2008-03-31
and once again

---

### Post by Dr Small on 2008-03-31
As for A. and B.:
```
cat /var/log/auth.log | grep SSHD
```

For C. and D., stuff is encrypted, so you won't be able to see what they access, and I have no clue about when they logout.

Also, check:
```
last
```

---

