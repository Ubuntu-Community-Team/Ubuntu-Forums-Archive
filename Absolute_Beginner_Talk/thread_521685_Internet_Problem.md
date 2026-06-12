---
title: "Internet Problem"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by amikhal on 2007-08-09
Hey y'all

Im pretty new here and I just installed ubuntu 6.10 on my dell desktop. I plugged the ethernet cable in which I know works fine, but I cant connect to the internet. What should i do?

---

### Post by oilchangeguy on 2007-08-09
> **amikhal said:**
> Hey y'all

Im pretty new here and I just installed ubuntu 6.10 on my dell desktop. I plugged the ethernet cable in which I know works fine, but I cant connect to the internet. What should i do?

have you reset the modem? (turned it off, then back on)

---

### Post by wormser on 2007-08-09
Here are a few things to try.  Applications> Accessories> Terminal

Post the results:
```
ifconfig
```

```
ping yahoo.com
```

```
ping 66.94.234.13
```

---

### Post by amikhal on 2007-08-09
I had this problem a while ago and just replaced the ethernet card in the computer with no success on either account. I am thinking i may have a static ip but how do i know for sure?

---

### Post by wormser on 2007-08-09
Try the things in my other post.  Also, can you describe how you are connected.  Who is the service provider, do you have a router, etc...

---

### Post by MenZa on 2007-08-09
I've personally had a lot of problems with the Avahi daemon. I used to reboot until it worked (it always would eventually), then stopped the avahi-daemon script from running at startup.

---

