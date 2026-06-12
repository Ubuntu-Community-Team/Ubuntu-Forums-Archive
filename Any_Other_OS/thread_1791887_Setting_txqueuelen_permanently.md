---
title: "Setting txqueuelen permanently"
date: 2011-06-27
forum: Any Other OS
---

### Post by luceerose on 2011-06-27
I want to set my txqueuelen to 10000 permanently on eth1. I've just read 4 different ways to do it.
Which way is the most appropriate ?

/etc/rc.local
```
/sbin/ifconfig eth1 txqueuelen 10000
```
/etc/network/interfaces
```
up ifconfig $IFACE txqueuelen 10000
```

```
sudo ip link set eth1 txqueuelen 10000
```

```
sudo ifconfig eth1 txqueuelen 10000
```

---

### Post by poolet on 2011-06-28
in my opinion is better to use the first one.... 

/etc/rc.local
```
/sbin/ifconfig eth1 txqueuelen 10000
```


the reason is because you add your txwueuelen directly at rc.local 
without involve your interfaces.....

---

### Post by luceerose on 2011-06-28
Thanks.
I also posted this question on the Debian & Mint forums.
Across all 3 forums you are the only person to answer in the entire 24hours since I posted.
I went with the first method & edited rc.local

---

