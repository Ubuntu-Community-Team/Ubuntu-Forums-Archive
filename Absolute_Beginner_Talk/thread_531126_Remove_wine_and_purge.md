---
title: "Remove wine and purge???"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by darren1270 on 2007-08-21
Quick question.... can someone post a code to remove and or purge wine???

---

### Post by Hobo Joe on 2007-08-21
```

sudo aptitude purge wine

```

---

### Post by darren1270 on 2007-08-21
Thank you Hobo

Darren

---

### Post by Hobo Joe on 2007-08-21
> **darren1270 said:**
> Thank you Hobo

Darren

Glad to be of service! :)

---

### Post by Dr Small on 2007-08-21
And for apt-get, it is
```
sudo apt-get remove wine --purge
```
Right?

---

### Post by nvteighen on 2007-08-21
> **Dr Small said:**
> And for apt-get, it is
```
sudo apt-get remove wine --purge
```
Right?
Yes.

(I also had the doubt, so installed "mailx" and then removed it with --purge)

---

