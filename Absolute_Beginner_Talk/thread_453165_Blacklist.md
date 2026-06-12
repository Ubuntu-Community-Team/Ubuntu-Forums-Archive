---
title: "Blacklist"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by GBee on 2007-05-24
I am very fresh with this Ubuntu life, so here's my first newbie question.

I've blacklisted bcm43xx in an attempt to get wireless running (ndiswrapper), but have now tried an alternate method that works, but of course, i need to unblacklist bcm43xx.

I'm sure this isn't hard, and my thanks for any reply!

---

### Post by renzokuken on 2007-05-24
run

```
gksudo gedit /etc/modprobe/blacklist
```

and comment out or delete the line referring to bcm3xx

it should be 

blacklist bcm3xx

and to unblacklist it change it to

# blacklist bcm3xx

---

### Post by GBee on 2007-05-24
Thanks for your help!

---

