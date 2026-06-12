---
title: "internet connection"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by newbe2007 on 2007-02-05
I just insert the CD to my computer CD and I want to "play"
with ubuntu befor installing it.
the network is o.k. (i can see my home network)
but i can not surf the internet with firefox
I have a router and i do not have a static ip
could i do something ?
I have a connection to my router (I can enter my route thru firefox) but that's all,
I can not exit to the internet !!
any suggestions ?
regards

---

### Post by kingmonkey on 2007-02-05
Is the internet connection on the router set up properly?

---

### Post by dustman on 2007-02-05
> **kingmonkey said:**
> Is the internet connection on the router set up properly?

yo ....can  u please tell me where I can start  a new thread regarding an issue I have with the grub loader? Thanks!

---

### Post by kingmonkey on 2007-02-05
> **dustman said:**
> yo ....can  u please tell me where I can start  a new thread regarding an issue I have with the grub loader? Thanks!

Absolute Beginners Talk - if thats what you are.

---

### Post by newbe2007 on 2007-02-05
With Windows XP I don't have any problem
any suggestions?

---

### Post by annda on 2007-02-05
do you get an IP address? if you type
```

ifconfig
```

under eth0 (if you are connected by cable) it should give you an inet addr: some numbers

also, can you ping?

terminal again:

```
ping -c 4 www.google.com
```

(this says: try four times)

---

