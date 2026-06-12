---
title: "Dell Inspiron 1000 Internet problems"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by btaf on 2008-02-14
I recently installed ubuntu 7.10 on my laptop, and now ive got it working. Problem is that even when i plug in an ethernet cable it wont get detected, and when typing "ifconfig eth1" into terminal all i get is "eth1: error fetching interface information: Device not found."  I've got a wireless card that plugs into the side slot area, but without internet i cant get ubuntu to recognize that. Help?

---

### Post by OffAxis on 2008-02-14
is eth1 your ethernet card?
eth0 is usually the first one.

try 
```
ifconfig
```

without the specific connection (eth1) and it'll list all available interfaces.

then

```
sudo dhclient eth0
```

where
eth0 = your actual connection

---

### Post by tritops on 2008-02-14
Hi there,
I know that Eth1 is for the wireless connection for your inspiron laptop.
try ifconfig eth0, and see if you were able to get an IP lease.

hth.
N

---

