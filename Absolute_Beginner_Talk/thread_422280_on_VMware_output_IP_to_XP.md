---
title: "on VMware output IP to XP"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Jun0 on 2007-04-25
hey everybody,
im new to linux
i installed a ubuntu 6.10 via VMware on my XP(simply text mode)
i use ADSL and get dynamic IP.
everytime that VMware ubuntu starts, it get a IP.
i need this data everytime.
(because i set a telnet service on it)
(i need this IP to telnet into it)
any simple way to output this ip to my host XP?(i cannot copy and paste it to my host XP after ifconfig )
OR
because it's a dynamic IP.
there any convenient way to telnet into it without that changing ip?
(i dont have fixed IP)

---

### Post by jhnthn on 2007-04-25
Either ifconfig, if you mean you want a local IP (like 192.168.0.1)

Or you could do
```
w3m www.whatismyip.com
```
if you mean your external IP (is that the right terminology?)

EDIT: Nevermind. Read your post wrong. I don't think this'll help

---

