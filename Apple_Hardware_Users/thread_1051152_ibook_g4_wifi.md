---
title: "ibook g4 wifi"
date: 2009-01-26
forum: Apple Hardware Users
---

### Post by DrFarnsworth on 2009-01-26
I finally got 8.4 on my ibook g4 and running correctly but for some reason I can not connect to any wifi I can see my router and it has 5 bars I am 2 feet from it. but i can not connect to it. any help would be great.

---

### Post by gletob on 2009-01-26
could you post the output of
```
sudo lshw -c NETWORK
```

---

### Post by DrFarnsworth on 2009-01-26
```
Hardware Lister (lshw) - B.02.12.01
Usage: lshw [-format] [-options ...]
       lshw -version

       -version         print program viersion (B.02.12.01)

```


is that what you are looking for  there is more under it with format can be  and options can be but i do not want to retype them all. 

I am doing some updates to see it that helps at all and the computer is running slow right now. So i am on my other one.

---

### Post by gletob on 2009-01-26
copying and pasting exactly whats in the box below should give me some info

```
sudo lshw -c NETWORK
```

---

