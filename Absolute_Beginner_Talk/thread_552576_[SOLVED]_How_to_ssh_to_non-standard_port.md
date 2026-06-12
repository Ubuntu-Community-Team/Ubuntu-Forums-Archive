---
title: "[SOLVED] How to ssh to non-standard port"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-09-16
Hi,

I changed the port number my ubuntu ssh-server lists to, to port 22022. How do I ssh to it?

I tried
```
ssh 192.168.0.6:22022
```and got
```
ssh: 192.168.0.6:22022: Name or service not known
```What command do I need to use?

Thanks.

---

### Post by Hospadar on 2007-09-16
try a "man ssh"  You should be able to find it in there

---

### Post by Dr Small on 2007-09-16
```
ssh 192.168.0.6 -p 22022
```

---

### Post by keymoo on 2007-09-16
Thanks I did look at the man page, but for some reason blindness prevented me from seeing the -p option.

---

