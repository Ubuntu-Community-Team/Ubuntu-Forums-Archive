---
title: "ftp?"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-11-06
Hello im using "places" on the menu between program and system then connect to server but it takes ages connecting to public ftp why? And when i try to use ftp in terminal window it says connected but im not i cant do anything inside :S

---

### Post by taurus on 2006-11-06
See if you can connect to it from a terminal!

```
ftp ip_address
```

---

### Post by haxer on 2006-11-06
it says im connected but nothing happens :S

---

### Post by taurus on 2006-11-06
What exactly is the message?  Make sure the other ftp server is up and running...

---

### Post by haxer on 2006-11-06
oem@haxer:~$ ftp
ftp> open 212.112.237.151
Connected to 212.112.237.151.



it says connected? :S

---

### Post by taurus on 2006-11-06
> **haxer said:**
> oem@haxer:~$ ftp
ftp> open 212.112.237.151
Connected to 212.112.237.151.



it says connected? :S
It means that it is trying to talk to the other machine!!!  If it is really connected, you should see a welcome message and a login prompt, asking for your login name!  

Please make sure the other machine has an ftp server running...

---

### Post by haxer on 2006-11-06
hmm.. sounds good to me :P haha.. omg so noobish forgive me :rolleyes:

---

