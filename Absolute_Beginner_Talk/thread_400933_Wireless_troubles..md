---
title: "Wireless troubles."
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Travelerr on 2007-04-04
I have been trying to get my wireless working for my laptop. According to...

```
lspci -l
```

I am running a Realtek 8185 Ethernet card

```
06:09.0 Ethernet controller: Realtek Semiconductor C., Ltd. Unknown device 8185 (rev 20)
```

I have tried installing the driver via linux distribution; What can I do to get wireless?

---

### Post by mahy on 2007-04-04
I'd say this is a normal ethernet card, not a wireless one. Does your wired connection work?

---

### Post by Travelerr on 2007-04-04
Yeah, I finally got it to work. I had to reset my connection. -duh-

Still gotta figure out this wireless thing.

I thought the lspci -v was specifically for finding your wireless. If not, that's good, and we can figure out how to locate the proper wireless card.

---

