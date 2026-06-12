---
title: "I broke it..."
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by CookieOrc on 2006-02-11
I was installing new packages... Yea bad idea. But i never learn untill I break it. I am unable to use the sudo APT-GET command anymore I get this error

> sudo: unable to lookup Peri.example.com via gethostbyname()


infact when I just type sudo it pops up that message. When I try to log into any of the package managers they pop up with an error that says 

> sh returned with an error

---

### Post by CookieOrc on 2006-02-11
I just realised that I cannot even get into administrator mode I get the same sh error.  I saw that my 127.0.0.1 loopback had the same Localhost Peri Peri.example.com

---

### Post by sjh on 2006-02-12
Had the same or similar problems when I pooched my /etc/hosts file.  It should read:

```
127.0.0.1	localhost.localdomain	localhost	ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Had to go in with a Live CD to restore it. 

(Used Knoppix and this guide:
[http://www-128.ibm.com/developerworks/linux/library/l-knopx.html?ca=dgr-lnxw82KNOPPIX](http://www-128.ibm.com/developerworks/linux/library/l-knopx.html?ca=dgr-lnxw82KNOPPIX))

Hope this helps
SJH

---

