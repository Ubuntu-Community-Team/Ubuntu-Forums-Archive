---
title: "How do i change the IP numbder on dapper?"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by K-J on 2006-07-14
How do i change the IP numbder on dapper?

---

### Post by MrHorus on 2006-07-14
```
sudo ifconfig <ipaddress>
```

Where <ip address> is the IP you want.

---

### Post by K-J on 2006-07-14
Can you please give me more detailed information (i tried ubuntu/Linux for the first time in my life today)

---

### Post by Loki1989 on 2006-07-14
> **K-J said:**
> Can you please give me more detailed information (i tried ubuntu/Linux for the first time in my life today)
like wise

---

### Post by MrHorus on 2006-07-14
Okay, open up a terminal/console from the menu bar.

Once it is open, type in that command I stated before.

you will be asked to type in your login password and once you do so, the IP address will be changed.

Also, the command before was slightly incorrect - here is the correct one:

```
sudo ifconfig eth0 <ip address>
```

Assuming eth0 is the Ethernet interface that you wish to set an IP address for.

If you wish to know anything else feel free to ask.

---

### Post by stoffepojken on 2006-07-14
/etc/network/interfaces ?

---

