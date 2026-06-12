---
title: "terminal updating"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-11-03
ive locked my Wine version to an older version.

when i do sudo apt-get upgrade

it insists on upgrading wine, how do i stop it doing this in terminal?

---

### Post by eph1973 on 2007-11-03
You could try installing wajig first:
```

sudo apt-get install wajig

```
Then use that to put wine on hold in apt:
```

sudo wajig hold wine

```
If you want to take it off hold, just enter
```

sudo wajig unhold wine

```
This seemed like the simplest solution for you to me.

---

### Post by SOULRiDER on 2007-11-03
Aptitude is already on your system, you dont need to install any additional programs. Just do a sudo aptitude hold wine

---

### Post by skymera on 2007-11-03
cool thanks hat worked :D

---

