---
title: "gaim only works sometimes"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by stefenkillsit on 2006-03-18
sometimes when I start my computer, the gaim will log on automatically and nothing goes wrong, although other times I start up my computer and gaim won't log on, it times out.

what can I do to fix this?

---

### Post by Pragmatist on 2006-03-19
Do you have the problem when you manually start Gaim, or only when using the automatic login feature?

---

### Post by stefenkillsit on 2006-03-19
both

---

### Post by Pragmatist on 2006-03-19
What happens if you use a dotted quad instead of the url domain name?  You can find the dotted quad by typing:
```
ping YourURL
```
So if I wanted to find hotmail's dotted quad I can do this:
> myusername@ubuntu:~/RealPlayer $ ping [www.hotmail.com](www.hotmail.com)
PING [www.hotmail.aate.nsatc.net](www.hotmail.aate.nsatc.net) (206.24.192.250) 56(84) bytes of data.
64 bytes from 206.24.192.250: icmp_seq=1 ttl=48 time=84.8 ms
64 bytes from 206.24.192.250: icmp_seq=2 ttl=48 time=85.2 ms
64 bytes from 206.24.192.250: icmp_seq=3 ttl=48 time=85.2 ms
64 bytes from 206.24.192.250: icmp_seq=4 ttl=48 time=85.4 ms


So we see the dotted quad corresponding to [www.hotmail.com](www.hotmail.com) is 206.24.192.250

---

