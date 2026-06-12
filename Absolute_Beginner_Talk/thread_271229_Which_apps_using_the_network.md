---
title: "Which apps using the network?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Kirky_D on 2006-10-04
I have installed gdesklets, and have a network monitor installed.

I noticed that my incoming connection was consistently around 50 kB/s.

Also system monitor shows the same

I am at uni, with a connection of 10 Mb/s so the whole connection is not being utilised.

But the traffic is enough to warrant concern. I was just wondering whether there is a way of finding what app or service in particular is eating up the bandwidth?

Cheers for any help!

---

### Post by elettronicha on 2006-10-04
Try this command

```
netsat -taup
```

for more infos about netstat

```
man netstat
```

---

